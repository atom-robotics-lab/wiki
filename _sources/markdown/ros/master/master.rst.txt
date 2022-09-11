ROS Master
==========

-  As you know ROS Nodes are building blocks of any ROS Application. A
   single ROS Application may have multiple ROS Nodes which communicate
   with each other.
-  The role of the ROS Master is to enable individual ROS nodes to
   locate one another.
-  Once these nodes have located each other they communicate with each
   other peer-to-peer.
-  The ROS Master provides naming and registration services to the rest
   of the nodes in the ROS system.
-  You can say, communication is established between nodes by the ROS
   Master. So, without ROS Master running ROS Nodes can not communicate
   with each other.

Start the ROS Master
====================

To start the ROS Master just enter in the terminal

.. code:: shell

   roscore

The above command will start three things

So roscore will start the following:

1. ROS Master
2. ROS Parameter Server
3. rosout Logging Node

.
