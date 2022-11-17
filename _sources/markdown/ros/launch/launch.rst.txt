****************
ROS Launch Files
****************
.. contents:: Table of Contents

-  In the previous sections you must have noticed that we need to use
   roscore command to
-  This is a tedious process to manually run nodes and load parameters.
-  Launch ﬁles provides the capability to do all these stuﬀ using a
   single command.
-  The idea is to mention all the nodes that you want to run, all the
   conﬁg ﬁle that you want to load etc in a single ﬁle which you can run
   using roslaunch command.


Create a ROS Launch file
========================

roslaunch Command
-----------------

-  roslaunch is a tool for easily launching multiple ROS nodes locally
   and remotely via SSH.

-  It includes options to automatically respawn processes that have
   already died. roslaunch takes in one or more XML conﬁguration ﬁles
   (with the .launch extension) that specify the parameters to set and
   nodes to launch.

Usage:

.. code:: shell

   roslaunch <package> file.launch

-   is nothing but the package name which you have created using
   catkin_create_pkg command or used any other package

Steps to create a launch file
-----------------------------

-  After creating a package, create a folder in the package names as a
   launch folder to store all the launch files in that folder.

.. code:: shell

   cd ~/catkin_ws/src/<package>
   mkdir launch

-  Here we can create launch ﬁles by running this command by going into
   the launch directory, we can keep any name for the launch ﬁle

.. code:: shell

   cd launch
   touch filename.launch

Now you can edit your launch ﬁle by adding diﬀerent nodes that you have
to run simultaneously.

Steps to add a ROS node in the launch ﬁle
-----------------------------------------

-  

   1. Launch ﬁles always starts with

``<launch>`` and end with ``</launch>``

-  2.Now to add any executable ﬁle which we have seen in the
   rosrun_command section, we have to add this line

.. code:: xml

   <node pkg="name_of_package" type="name_of_executable.py" name="name_of_executable" output="screen"/>

-  name is the name of the node which is created in that executable
-  output means it will print the data given to the roslog command
-  type is the name of executable ﬁle
-  pkg is the package name which you have created.

Steps to load Conﬁg YAML ﬁle in ROS Parameter Server
----------------------------------------------------

You can use rosparam tag to load the YAML ﬁle.

-  type is the name of executable ﬁle

-  pkg is the package name which you have created

-  name_of_package is the name of your ROS package.

-  config.yaml is the name of your conﬁguration ﬁle.

Steps to add a shell script in the launch file
----------------------------------------------

You can use node tag to run any shell script using launch ﬁle

.. code:: xml

   <node pkg="name_of_package" type="shell_script.sh" name="shell_script" output="screen">
       <param name="cmd" value="$(find name_of_package)/launch/shell_script.sh"/>
   </node>

-  name_of_package is the name of your ROS package.
-  shell_script.sh is the name of your conﬁguration ﬁle.
-  /launch/shell_script.sh is the location of the shell script inside
   your ROS Package folder.

Example
=======

Example 1: Launch two ROS Nodes
-------------------------------

Aim
^^^

-  To launch talker and listener node present in rospy_tutorials
   package.

-  For this create a chatter.launch ﬁle and save it in the launch folder
   inside pkg_ros_basics package.

.. NOTE:: To install rospy_tutorials package in your system you can run

.. code:: shell

   sudo apt-get install ros-noetic-ros-tutorials this command.

-  Once installed, you can use listener python script and talker
   executable written in C++ present in rospy_tutorials package.

Code
^^^^

chatter.launch

.. code:: xml

   <launch>
   <node name="talker" pkg="rospy_tutorials" type="talker" output="screen"/>
   <node name="listener" pkg="rospy_tutorials" type="listener.py" output="screen"/>
   </launch>

-  Here ﬁrst talker.cpp ﬁle (for cpp ﬁle we dont need to add .cpp
   extension) has been included with the node name as talker and also
   set output as screen so you can see the output from talker node.
-  Next we have added listener.py which has node name as listener and
   here also we have set output as screen.

Run Command
^^^^^^^^^^^

Now run these command to run the launch ﬁle,

.. code:: shell

   roslaunch pkg_ros_basics chatter.launch

Example 2: Launch turtle in forest
----------------------------------

Aim
^^^

-  To write a launch ﬁle to run turtlesim_node node and
   turtle_teleop_key node present in turtlesim package.
-  While launching the turtlesim_node make sure to change the background
   colour of the simulator from blue to forest green.
-  Name the launch ﬁle turtlesim.launch and save it in launch folder
   inside pkg_ros_basics package.

Code
^^^^

turtlesim.launch

.. code:: xml

   <launch>
   <node pkg="turtlesim" type="turtlesim_node" name="node_turtlesim_node">
   <param name="/turtlesim_node/background_r" value="34" />
   <param name="/turtlesim_node/background_g" value="139" />
   <param name="/turtlesim_node/background_b" value="34" />
   <param name="/background_r" value="34" />
   <param name="/background_g" value="139" />
   <param name="/background_b" value="34" />
   </node>
   <node pkg="turtlesim" type="turtle_teleop_key" name="node_turtle_teleop_key" />   
   </launch>

Run Command
^^^^^^^^^^^

.. code:: shell

   roslaunch pkg_ros_basics turtlesim.launch

Example 3: Load YAML
--------------------

Aim
^^^

-  To write a launch ﬁle to load config_my.yaml present in
   pkg_ros_basics package.
-  Also launch the node_param_get_set.py ROS node after loading the YAML
   ﬁle.

Code
^^^^

load_yaml.launch

.. code:: xml

   <launch>
   <rosparam file ="$(find pkg_ros_basics)/config/config_my.yaml"/>
   <node pkg="pkg_ros_basics" type="node_param_get_set.py" name="node_param_get_set">
   </launch>

Run Command
^^^^^^^^^^^

.. code:: shell

   roslaunch pkg_ros_basics load_yaml.launch

