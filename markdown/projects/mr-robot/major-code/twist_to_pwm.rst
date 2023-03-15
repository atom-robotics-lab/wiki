Twist To PWM
============

This code is a Python script that implements a ROS node for a differential drive robot. The robot is controlled using velocity commands sent to the ``/cmd_vel`` topic and feedback on the actual wheel speeds is obtained from the ``/left_speed`` and ``/right_speed`` topics.

The DifferentialDriver class is defined to encapsulate the functionality of the node. The constructor initializes the ROS node and sets up the necessary subscribers and publishers for the topics. It also reads various parameters related to the robot's physical properties and calculates the maximum speed that the robot can achieve.

.. code:: python
     
     def __init__(self):

        rospy.init_node('cmdvel_listener', anonymous=False)
        rospy.Subscriber("/cmd_vel", Twist, self.callback)
        rospy.Subscriber("left_speed", Float64, self.update_left)
        rospy.Subscriber("right_speed", Float64, self.update_right)

        self.left_pwm_pub = rospy.Publisher('left_pwm', Int32, queue_size=10)
        self.right_pwm_pub = rospy.Publisher('right_pwm', Int32, queue_size=10)

        self.left_pwm = Int32()
        self.right_pwm = Int32()

        self.params_setup() 
        self.wheel_radius = self.wheel_diameter/2
        self.circumference_of_wheel = 2 * pi * self.wheel_radius
        self.max_speed = (self.circumference_of_wheel*self.motor_rpm)/60   # m/sec
        self.right_vel_actual = 0
        self.left_vel_actual = 0
        self.kp = 0.5


This is the constructor method of the DifferentialDriver class. This method is called when an object of the class is created. In this method, we initialize the ROS node, create subscribers and publishers for topics ``/cmd_vel, left_speed, right_speed, left_pwm and right_pwm``. We also call the method ``params_setup()`` to read the parameter values from the ROS parameter server and set the instance variables of the class DifferentialDriver.

.. code:: python
    
    def params_setup(self) :
        self.motor_rpm = rospy.get_param("mr_robot_firmware/motor_rpm")
        self.wheel_diameter = rospy.get_param("mr_robot_firmware/wheel_diameter")
        self.wheel_diameter = self.wheel_diameter/100
        self.wheel_separation = rospy.get_param("mr_robot_firmware/wheel_diameter")
        self.wheel_separation = self.wheel_separation/100
        self.max_pwm_val = rospy.get_param("mr_robot_firmware/twist_max_pwm")
        self.min_pwm_val = rospy.get_param("mr_robot_firmware/twist_min_pwm")

This method reads the parameter values from the ROS parameter server and sets the instance variables of the class DifferentialDriver. 

.. note::
    
    The parameters read and their respective instance variables are:

    mr_robot_firmware/motor_rpm: motor_rpm
    mr_robot_firmware/wheel_diameter: wheel_diameter
    mr_robot_firmware/wheel_separation: wheel_separation
    mr_robot_firmware/twist_max_pwm: max_pwm_val
    mr_robot_firmware/twist_min_pwm: min_pwm_val
    
    All the parameter values are read as float values and converted to the required units and are taken from ``mr_robot_firmware.yaml``

.. code:: python

    def update_left(self, speed):
        self.left_vel_actual = speed.data

This method is called whenever a new message is received on the topic ``/left_speed``. It updates the instance variable ``/left_vel_actual`` with the received value of speed.

.. code:: python

    def update_right(self, speed):
        self.right_vel_actual = speed.data

This method is called whenever a new message is received on the topic ``/right_speed``. It updates the instance variable ``/right_vel_actual`` with the received value of speed.

.. code:: python

    def stop( self ):
        self.change_duty_cycle(0, 0 , 0 , 0)       

This method sets the PWM values for both the motors to zero, effectively stopping the robot. It calls the ``change_duty_cycle()`` method with zero values for both left and right PWM values.

.. code:: python

    def get_pwm(self, left_speed, right_speed):
        
        self.lspeedPWM = max(min((left_speed/self.max_speed)*self.max_pwm_val, self.max_pwm_val), self.min_pwm_val)
        self.rspeedPWM = max(min((right_speed/self.max_speed)*self.max_pwm_val,self.max_pwm_val), self.min_pwm_val)

        return self.lspeedPWM, self.rspeedPWM

This method calculates the required PWM values for both the motors based on the given linear and angular velocities of the robot. The formula used is ``(velocity / max_speed) * max_pwm_val``, where velocity can be either left or right wheel velocity and max_speed is the maximum possible speed of the robot. The calculated PWM values are limited to be within the range of **min_pwm_val** and **max_pwm_val**.

.. code:: python

    def correct_pwm(self, left_vel, right_vel, pwm_left, pwm_right):
        try:
            r_error = right_vel - self.right_vel_actual
            l_error =  left_vel - self.left_vel_actual 
            pwm_left = pwm_left + l_error*self.kp
            pwm_right = pwm_right + r_error*self.kp
        except:
            pass

This method is used to correct the calculated PWM values for the left and right motors based on the actual velocities of the motors as received from the topics ``/left_speed`` and ``/right_speed``. The proportional gain kp is used to calculate the correction values. The corrected PWM values are returned by this method.

.. code:: python

    def callback(self, data):  

        linear_vel = data.linear.x                                              # Linear Velocity of Robot
        angular_vel = data.angular.z                                            # Angular Velocity of Robot

        right_vel = linear_vel + (angular_vel * self.wheel_separation) / 2      # right wheel velocity
        left_vel  = linear_vel - (angular_vel * self.wheel_separation) / 2      # left wheel velocity

        print(" Left Velocity = {}  |   Right Velocity = {}  |   Left Actual = {}    |   Right Actual = {}".format(left_vel, right_vel, self.left_vel_actual, self.right_vel_actual))
        
        left_pwm_data , right_pwm_data = self.get_pwm(left_vel, right_vel)
        try:
            left_pwm_data , right_pwm_data = self.correct_pwm(left_vel, right_vel, left_pwm_data , right_pwm_data)
        except:
            pass
        #print(left_pwm_data) 
        #print(right_pwm_data) 


        self.left_pwm.data = int(left_pwm_data)
        self.right_pwm.data = int(right_pwm_data)


        self.left_pwm_pub.publish(self.left_pwm)
        self.right_pwm_pub.publish(self.right_pwm)

This method is called whenever a new message is received on the topic ``/cmd_vel``. It calculates the left and right wheel velocities based on the linear and angular twist velocities, and then calculates the PWM values for both the motors using the ``get_pwm()`` method. The PWM values are then corrected using the ``correct_pwm()`` method, and the corrected PWM values are published on the topics ``/left_pwm`` and ``/right_pwm`` using the ``/left_pwm_pub`` and ``/right_pwm_pub`` publishers, respectively. The method also prints the calculated and actual velocities of both the wheels for debugging purposes.
