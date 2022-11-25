*********
ROS Nodes
*********

.. contents:: Table of Contents

-  A ROS Node is a piece of software/executable that uses ROS to
   communicate with other ROS Nodes.
-  ROS Nodes are building block of any ROS Application.
-  For example, if you have a wall-following robot then one ROS Node
   could get distance sensor values and another node can control the
   motors of the robot. So, these two nodes will communicate with each
   other in order to move the robot.
-  You can write your entire ROS Application in a single node but having
   multiple nodes ensures that if a node crashes it won’t crash your
   entire ROS application.
-  A ROS package can have multiple ROS Nodes.
-  Python and C++ are majorly used to write ROS Nodes.

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

.. NOTE:: roscd will work only if you have sourced setup.bash of your
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

Command 
=======

Command: rosrun
---------------

rosrun allows you to run an executable in an arbitrary package from
anywhere without having to give its full path or cd/roscd there ﬁrst.

Usage:

.. code:: shell

   rosrun <package> <executable>

``<package>`` is nothing but the package name which you have created
using catkin_create_pkg command or used any other package.

``<executable>`` is the python or cpp ﬁle.

To create an executable python file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

-  After creating a package, create a folder in the package names as
   scripts folder to store all the python ﬁles in that folder.

.. code:: shell

   cd ~/catkin_ws/src/<package>
   mkdir scripts

-  Here we can create python scripts by running this command by going
   into the scripts directory,

.. code:: shell

   cd scripts
   touch filename.py

-  Now you can edit your python ﬁle and before running you have to make
   it executable by running this command once,

.. code:: shell

   cd ~/catkin_ws/src/<package>/scripts
   chmod +x filename.py

-  Here we can create cpp ﬁles by running this command by going into the
   src directory,

.. code:: shell

   cd src
   touch filename.cpp

Now you can edit your cpp ﬁle , but for making it executable we have to
edit the CMakeLists.txt ﬁle

Add these few lines at the bottom of CMakeLists.txt ﬁle,

.. code:: xml

   add_executable(filename src/filename.cpp)
   target_link_libraries(filename ${catkin_LIBRARIES})

Then run this command,

.. code:: shell

   cd ~/catkin_ws
   catkin build

Command: rosnode
----------------

-  rosnode contains the rosnode command-line tool for displaying debug
   information about ROS Nodes.

.. Note:: For quick information about any command, be that outside of ROS,
simply type the command along with suﬃx –h or -help . This is a widely
used concept among other Linux Command: rosrun commands for quick
references. Here’s an example for rosnode –h command

-  .. rubric:: list
      :name: list

rosnode list displays a list of all current nodes.

Let’s ﬁgure out what argument the list sub-command needs. In a new
terminal run start the rosmaster:

.. code:: shell

   roscore

And in another terminal, run:

.. code:: shell

   rosrun rospy_tutorials talker

And in another terminal, run:

.. code:: shell

   rosnode list

Now the node named talker (node with word talker in it) will be printed
on the terminal.

-  .. rubric:: info
      :name: info

-  rosnode info /node_name displays information about a node, including
   publications and subscriptions.

-  Let’s ﬁgure out what argument the info sub-command needs. In a new
   terminal run start the

.. code:: shell

   rosmaster

And in another terminal, run:

.. code:: shell

   rosrun rospy_tutorials talker

And in another terminal, run:

.. code:: shell

   rosnode info <talker_node>

This should give details of the particular node

-  .. rubric:: kill
      :name: kill

.. IMPORTANT:: rosnode kill is not guaranteed to succeed.

-  Let’s ﬁgure out what argument the kill sub-command needs. In a new
   terminal run start the rosmaster:

.. code:: shell

   roscore

-  And in another terminal, run:

.. code:: shell

   rosrun rospy_tutorials talker

-  And in another terminal, run:

.. code:: shell

   rosnode kill rosout <talker_node>
