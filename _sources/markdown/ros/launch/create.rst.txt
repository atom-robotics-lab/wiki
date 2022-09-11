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
