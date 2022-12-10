***********
ROS Package
***********

Software in ROS is organized in packages. A package might contain ROS nodes, a ROS-
independent library, a dataset, conﬁguration ﬁles, a third-party piece of software, or
anything else that logically constitutes a useful module. The goal of these packages it to
provide this useful functionality in an easy-to-consume manner so that software can be
easily reused. In general, ROS packages follow a "Goldilocks" principle: enough
functionality to be useful, but not too much that the package is heavyweight and diﬃcult
to use from other software.

Create a ROS package
====================

This tutorial will demonstrate how to use the catkin_create_pkg script
to create a new catkin package, and what you can do with it after it has
been created.

1. First, navigate to the source space directory of the catkin workspace
   you’ve created.

.. code:: shell

   cd ~/catkin_ws/src

2. Now, use the catkin_create_pkg script to create a new package called
   pkg_ros_basics which depends on std_msgs, roscpp, and rospy:

.. code:: shell

   catkin_create_pkg pkg_ros_basics std_msgs rospy roscpp

-  This will create a beginner_tutorials folder which contains a
   package.xml and a CMakeLists.txt , which have been partially ﬁlled
   out with the information you gave catkin_create_pkg .

-  catkin_create_pkg requires that you give it a package_name and
   optionally a list of dependencies on which that package depends:
   catkin_create_pkg [depend1] [depend2] [depend3]

3. Now, you need to build the packages in the catkin workspace

.. code:: shell

   cd ~/catkin_ws
   catkin_make

-  Inside the package, there are src folder, package.xml ,
   CMakeLists.txt , and the include folders.

   -  CMakeLists.txt: This ﬁle has all the commands to build the ROS
      source code inside the package and create the executable. For more
      information about CMakeLists visit here. package.xml: This is an
      XML ﬁle. It mainly contains the package dependencies information,
      and so forth.
   -  src: The source code of ROS packages are kept in this folder.
   -  package.xml : This file mainly contains the package dependencies
      ,information etc.


