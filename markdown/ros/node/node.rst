ROS Nodes
=========

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
