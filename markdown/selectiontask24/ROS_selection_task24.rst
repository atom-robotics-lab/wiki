ROS Selection Task 2024-2025
============================


Problem statement
-----------------

-  The objective of the task is to move the turtle inside the turtlesim 
   window in a vertical Candy shape 

-  To acheive this task you are supposed to create a node named
   /node_turtle_move within a python script,
   node_turtle_move.py



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
   new to ROS2.

.. Warning::
   The **Deadline** for completing the task: **9th October, 2024**

Expected Output
---------------

.. raw:: html

   <center><iframe width="560" height="315" src="https://www.youtube.com/embed/ja-QRX4gu6E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center><br>


.. Note:: THE Candy SHOULD BE VERTICAL .

Hints
-----

-  The turtle needs to move in a vertical Candy shape .

-  You can refer `POSE <https://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/Pose.html>`__ to learn more about pose function.

-  You can refer `TWIST <https://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/Twist.html>`__ to learn more about twist function.

-  Use linear velocity and angular velocity to get this done.

-  Keep tracking the distance travelled so as to know when to stop. You
   can refer to Overview of rospy for more hint

Sample Code Snippet
-----------------------

**Question:** Write a python code to move ROS's turtlesim bot on a straight path 
while bot's distance is less than 6.

.. code-block:: python

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
-----------------------

.. raw:: html

   <center><iframe width="560" height="315" src="https://www.youtube.com/embed/tjGNhEe-S_k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center><br>

Commands used:

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
   you'll create a python script, named node_turtle_move.py.
-  Fill the script with proper programming ethics. Doing this will help
   us understand your code better and quicker than usual.
-  After completing the python script. Make it executable, if it isn't
   already. To do that, enter the following code.

.. code:: shell

   cd ~/turtle_ws
   colcon_build
   source install/setup.bash

-  You can either run them in separate terminals or
   simply create a selection_task.launch file inside the
   ``~/turtle_ws/src/selection_task/launch/`` folder. Launch file can
   run multiple nodes unlike a python/cpp script. Run the launch file,
   enter, This should run three processes in parallel.

-  turtlesim_node

-  node_turtle_move.py

.. seealso::
   Please refer to the tutorials and resouces given in the wiki or visit
   the official `ROSWIKI <http://wiki.ros.org/Documentation>`__ if you
   need help with anything regarding ROS2.

 
