ROS Selection Task
========================


Problem statement
-----------------

-  The objective of the task is to move the turtle inside the turtlesim 
   window in a vertical D shape of radius 1 unit.

-  To acheive this task you are supposed to create a node named
   /node_turtle_revolve within a python script,
   node_turtle_revolve.py



   Dont worry if you are new to ROS or Linux(Ubuntu), the task
   is fairly simple and we have provided you with ample resource and
   tutorials in this WIKI to the complete this task so only a strong
   will and a little bit of brains is required to get the work done.
   Also even though this just a weekend task we have provided ample
   amount of time as we also have our midterm exams during this time. So
   we think a week time is enough so you guys can give your exams freely
   and manage your time in order to complete the task

.. Note:: All the resources to complete the said task are provided in
   the ROS section of ATOM WIKI. So make sure to check it out if you are
   new to ROS.

.. seealso::
   The deadline for completing the task: 11th December, 2022 Head to the
   Problem statement section to begin with the task.

Expected Output
---------------

.. raw:: html

   <iframe width="640" height="480" src="https://www.youtube.com/embed/lwI40jNR-D4" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen>

.. raw:: html

   </iframe>

.. Note:: THE TURTLE SHOULD STOP AT THE INITIAL POINT ONLY.

Hints
-----

-  The turtle needs to move in a vertical ‘D’ shape with a radius of 1 unit
   during its sem-circular motion.
   
-  Use linear velocity as well as angular velocity with some combination
   to get this done.

-  Keep tracking the distance travelled so as to know when to stop. You
   can refer to Overview of rospy for more hint

Sample Code Snippet
*******************

**Question:** Write a python code to move ROS's turtlesim bot on a straight path 
while bot's distance is less than 6.

.. code:: python

   #! /usr/bin/env python3

   import rospy
   from geometry_msgs.msg import Twist
   from turtlesim.msg import Pose
   
   my_X = 0 
   my_Y = 0
   x_dist = 6
   
   # Subscriber Callback that gives position of the turtle (x & y)
   def pose_callback(pose): 
   
              global my_X, my_Y
              rospy.loginfo("Robot X = %f: Robot Y=%f\n",pose.x,pose.y)
              my_X = pose.x
              my_Y = pose.y
              
   def move_turtle(lin_vel):  
        
       global my_X
       rospy.init_node('move_turtle', anonymous=True)
       pub = rospy.Publisher('/turtle1/cmd_vel', Twist, queue_size=10)
       rospy.Subscriber('/turtle1/pose',Pose, pose_callback)
   
       rate = rospy.Rate(10) # 10hz    
       vel = Twist()
       while not rospy.is_shutdown():
   
           vel.linear.x = lin_vel
           vel.linear.y = 0
           vel.linear.z = 0
           vel.angular.x = 0
           vel.angular.y = 0
           vel.angular.z = 0
   
           rospy.loginfo("Linear Vel = %f: ", lin_vel)
   
           # Stop the turtle when it reaches x_dist
           if(x_dist < my_X ):
                   rospy.loginfo("Turtle Reached destination")
                   rospy.logwarn("Stopping Turtle")
                        
                   break
   
           pub.publish(vel)
           rate.sleep()
   
   move_turtle(2.0)

Output video
*************

.. raw:: html

   <iframe width="640" height="480" src="https://youtube.com/embed/qZ2wQTCKW0s" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen>

.. raw:: html

   </iframe>

.. code:: shell
   roscore
   rosrun turtlesim turtlesim_node
   rosrun package_name script_name

Procedure
---------

Follow the instructions given below to get started with the task.

-  First, you will need to create a package named selection_task within
   your ROS workspace. Once your package is created, source and build
   your workspace.
-  Within this package, you should have a 'scripts' folder inside which
   you'll create a python script, named node_turtle_revolve.py.
-  Fill the script with proper programming ethics. Doing this will help
   us understand your code better and quicker than usual.
-  After completing the python script. Make it executable, if it isn't
   already. To do that, enter the following code.

.. code:: shell

   cd ~/catkin_ws
   catkin build
   source devel/setup.bash
   chmod +x ~/catkin_ws/src/selection_task/scripts/node_turtle_revolve.py

-  Before executing make sure that roscore is running along with
   turtlesim_node. You can either run them in separate terminals or
   simply create a selection_task.launch file inside the
   ``~/catkin_ws/src/selection_task/launch/`` folder. Launch file can
   run multiple nodes unlike a python/cpp script. Run the launch file,
   enter, This should run three processes in parallel.

-  roscore

-  turtlesim_node

-  node_turtle_revolve.py

.. seealso::
   Please refer to the tutorials and resouces given in the wiki or visit
   the official `ROSWIKI <http://wiki.ros.org/Documentation>`__ if you
   need help with anything regarding ROS.

 
