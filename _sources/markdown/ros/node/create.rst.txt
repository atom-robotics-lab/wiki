Creating a ROS Node
===================

-  In this section we will learn how to create a ROS Node inside
   pkg_ros_basics ROS Package which we created in the previous section.

-  Navigate to pkg_ros_basics

.. code:: shell

   cd ~/catkin_ws/src/pkg_ros_basics

OR

.. code:: shell

   roscd pkg_ros_basics

*NOTE:* roscd will work only if you have sourced setup.bash of your
catkin workspace.

-  Create a scripts folder for your Python scripts and navigate into the
   folder.

.. code:: shell

   mkdir scripts
   cd scripts

-  Create a Python script called node_hello_ros.py .

.. code:: shell

   touch node_hello_ros.py

-  Open the script in any text-editor and start editing.

.. code:: shell

   gedit node_hello_ros.py

-  First line of all your Python ROS scripts should be the following
   shebang

.. code:: shell

   #!/usr/bin/env python

-  Now write a ROS Node to print Hello World! on the console.

.. code:: python

   #!/usr/bin/env python
   import rospy
   def main():
   #Initialize the new node
   rospy.init_node('node_hello_ros', anonymous=True)
   #  Print info on console.
   rospy.loginfo("Hello World!")

   if __name__ == '__main__':

       try:
           main()
       except rospy.ROSInterruptException:
           pass

-  Make your node executable

.. code:: shell

   sudo chmod +x node_hello_ros.py

-  Now to run your node

   -  Open the terminal and run ROS master

   .. code:: shell

      roscore

   -  Once the roscore is running open a new terminal and run the main
      node

   .. code:: shell

      rosrun pkg_ros_basics node_hello_ros.py

   .. note:: This command will work only if you have sourced setup.bash of your catkin workspace either manually or using .bashrc .
