ESP_diff_tf
===========

.. code:: python

    def __init__(self):

        rospy.init_node("diff_tf")
        self.nodename = rospy.get_name()
        rospy.loginfo("-I- %s started" % self.nodename)
        
        #### parameters #######
        self.rate = rospy.get_param('mr_robot_firmware/rate')  # the rate at which to publish the transform
        self.ticks_meter = float(rospy.get_param('mr_robot_firmware/ticks_meter'))  # The number of wheel encoder ticks per meter of travel
        self.base_width = float(rospy.get_param('mr_robot_firmware/base_width')) # The wheel base width in meters
        
        self.base_frame_id = rospy.get_param('mr_robot_firmware/base_frame_id') # the name of the base frame of the robot
        self.odom_frame_id = rospy.get_param('mr_robot_firmware/odom_frame_id') # the name of the odometry reference frame
        
        self.encoder_min = rospy.get_param('encoder_min', -2147483648)
        self.encoder_max = rospy.get_param('encoder_max', 2147483648)
        self.encoder_low_wrap = rospy.get_param('wheel_low_wrap', (self.encoder_max - self.encoder_min) * 0.3 + self.encoder_min )
        self.encoder_high_wrap = rospy.get_param('wheel_high_wrap', (self.encoder_max - self.encoder_min) * 0.7 + self.encoder_min )
 
        self.t_delta = rospy.Duration(1.0/self.rate)
        self.t_next = rospy.Time.now() + self.t_delta
        
        # internal data
        self.enc_left = None        # wheel encoder readings
        self.enc_right = None
        self.left = 0               # actual values coming back from robot
        self.right = 0
        self.lmult = 0
        self.rmult = 0
        self.prev_lencoder = 0
        self.prev_rencoder = 0
        self.x = 0                  # position in xy plane 
        self.y = 0
        self.th = 0
        self.dx = 0                 # speeds in x/rotation
        self.dr = 0
        self.then = rospy.Time.now()
        self.left_speed = 0
        self.right_speed = 0
        
        # subscriptions
        rospy.Subscriber("left_encoder", Int32, self.lwheelCallback)
        rospy.Subscriber("right_encoder", Int32, self.rwheelCallback)
        rospy.Subscriber("initialpose", PoseWithCovarianceStamped, self.update_pose)
        self.odomPub = rospy.Publisher("odom", Odometry,queue_size=10)
        self.left_speed_pub = rospy.Publisher("left_speed", Float64,queue_size=10)
        self.right_speed_pub = rospy.Publisher("right_speed", Float64,queue_size=10)
        self.odomBroadcaster = TransformBroadcaster()


In this part we specify basic parameter like **wheel encoder readings ,rate, base_width etc**. As well subscribing & publishing **encoder and odom values.** 

.. code:: python

    def update_pose(self, data):
    (roll, pitch, yaw) = euler_from_quaternion([data.pose.pose.orientation.x, data.pose.pose.orientation.y, data.pose.pose.orientation.z, data.pose.pose.orientation.w])
        self.x = data.pose.pose.position.x 
        self.y = data.pose.pose.position.y
        self.th = yaw

Inside the ``update_pose()`` method, the x, y, and z coordinates of the object's position are extracted from the data dictionary and stored in the self.position attribute of the PoseEstimator object. This attribute is a tuple that contains the x, y, and z coordinates of the object's position, respectively.

.. code:: python
    
    def update(self):
        now = rospy.Time.now()
        if now > self.t_next:
            elapsed = now - self.then
            self.then = now
            elapsed = elapsed.to_sec()
            

            # calculate odometry
            if self.enc_left == None:
                d_left = 0
                d_right = 0
            else:
                d_left = (self.left - self.enc_left) / self.ticks_meter
                d_right = (self.right - self.enc_right) / self.ticks_meter

            # calculate the velocity of the 2 wheels
            self.left_speed = self.left / elapsed
            self.right_speed = self.right / elapsed

            # print(d_left)
            # print(self.right_speed)

            self.left_speed_pub.publish(float(d_left))
            self.right_speed_pub.publish(float(d_right))

            self.enc_left = self.left
            self.enc_right = self.right
           
            # distance traveled is the average of the two wheels 
            d = ( d_left + d_right ) / 2
            # this approximation works (in radians) for small angles
            th = ( d_right - d_left ) / self.base_width
            # calculate velocities
            self.dx = d / elapsed
            self.dr = th / elapsed
           
    
This code segment is checking whether the current time now is greater than the next time to update the pose t_next. If the condition is True, it proceeds to calculate the elapsed time elapsed since the last pose update, using the now and then times stored in the class.
Then, the code calculates the odometry by determining the distance traveled by each wheel based on the change in encoder ticks since the last update. If the encoder ticks have not changed since the last update (i.e., enc_left is None), then the distance traveled by both wheels is set to 0.
Finally, the code calculates the speed of each wheel based on the distance traveled and the elapsed time, and stores them in ``left_speed`` and ``right_speed`` variables respectively.

.. code:: python

        if (d != 0):
                # calculate distance traveled in x and y
                x = cos( th ) * d
                y = -sin( th ) * d
                # calculate the final position of the robot
                self.x = self.x + ( cos( self.th ) * x - sin( self.th ) * y )
                self.y = self.y + ( sin( self.th ) * x + cos( self.th ) * y )
            if( th != 0):
                self.th = self.th + th
                
            # publish the odom information
            quaternion = Quaternion()
            quaternion.x = 0.0
            quaternion.y = 0.0
            quaternion.z = sin( self.th / 2 )
            quaternion.w = cos( self.th / 2 )
            self.odomBroadcaster.sendTransform(
                (self.x, self.y, 0),
                (quaternion.x, quaternion.y, quaternion.z, quaternion.w),
                rospy.Time.now(),
                self.base_frame_id,
                self.odom_frame_id
                )
            
            odom = Odometry()
            odom.header.stamp = now
            odom.header.frame_id = self.odom_frame_id
            odom.pose.pose.position.x = self.x
            odom.pose.pose.position.y = self.y
            odom.pose.pose.position.z = 0
            odom.pose.pose.orientation = quaternion
            odom.child_frame_id = self.base_frame_id
            odom.twist.twist.linear.x = self.dx
            odom.twist.twist.linear.y = 0
            odom.twist.twist.angular.z = self.dr
            self.odomPub.publish(odom)

This section of the code is responsible for calculating and publishing the odometry information of the robot.

If the robot has traveled a nonzero distance ``(d != 0)``, it calculates the distance traveled in the x and y directions using the current angle of the robot *(th)* and the distance traveled *(d)*. It then updates the position of the robot by adding this distance to the current position.

If the robot has turned a nonzero angle ``(th != 0)``, it updates the current angle of the robot *(self.th)* by adding the angle turned *(th)*.

Next, it creates a Quaternion object to represent the orientation of the robot, and sets its values based on the current angle of the robot.

Then, it publishes the odometry information as a transform from the base frame to the odometry frame, and as an Odometry message on the ``/odom`` topic, with the position and orientation of the robot.

.. code:: python

    def lwheelCallback(self, msg):
        enc = msg.data
        if (enc < self.encoder_low_wrap and self.prev_lencoder > self.encoder_high_wrap):
            self.lmult = self.lmult + 1
            
        if (enc > self.encoder_high_wrap and self.prev_lencoder < self.encoder_low_wrap):
            self.lmult = self.lmult - 1
    
        self.left = 1.0 * (enc + self.lmult * (self.encoder_max - self.encoder_min)) 
        self.prev_lencoder = enc

This is a callback function for the left wheel encoder subscriber. It receives a message from the topic to which it has subscribed, and extracts the data from it.

- ``enc = msg.data``: extracts the data from the message and stores it in the enc variable.
- ``if (enc < self.encoder_low_wrap and self.prev_lencoder > self.encoder_high_wrap)``: checks if the encoder value has wrapped around the low end (underflow) and the previous value was above the high end (overflow). If true, increment the left encoder multiplier.
- ``if (enc > self.encoder_high_wrap and self.prev_lencoder < self.encoder_low_wrap)``: checks if the encoder value has wrapped around the high end (overflow) and the previous value was below the low end (underflow). If true, decrement the left encoder multiplier.
- ``self.left = 1.0 * (enc + self.lmult * (self.encoder_max - self.encoder_min))``:** calculates the left encoder count by adding the current encoder value to the left encoder multiplier times the range of the encoder values. The range is defined as the difference between the maximum and minimum encoder values.
- ``self.prev_lencoder = enc``: updates the previous encoder value with the current encoder value.



