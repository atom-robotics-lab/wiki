Machine Specification For MR Robot
==================================

Introduction
------------

In ROS (Robot Operating System), communication between different nodes (e.g., sensors, controllers, and other agents) is established through the use of a Master-Slave connection. The Master node acts as a central hub that manages the communication between different nodes, while the Slave nodes communicate with each other through the Master node.

Implementation of the machine specifications for MR Robot are set up to launch various nodes in accordance with their desired locations. For instance, while rosserial is launched on the Raspberry Pi to obtain serial data from the microcontroller, RVIZ should run in the Master because visualisation is required. So, it is possible to use a single launch file by naming nodes.

Master Bashrc file
------------------

.. code:: shell

    export ROS_MASTER_URI=http://localhost:11311/

This line sets the environment variable `ROS_MASTER_URI`, which specifies the URI (Uniform Resource Identifier) of the ROS master node. In this case, the URI is set to `http://localhost:11311/`, which means that the master node is running on the same machine as the current node, and it is accessible using the HTTP protocol at port `11311`. The master node is responsible for managing the communication between different nodes in ROS.

.. code:: shell

    export ROS_HOSTNAME=[hostname]  

This line sets the environment variable `ROS_HOSTNAME`, which specifies the hostname of the current node. In this case, the hostname should be set to the hostname of the machine running the current node. This variable is used by other nodes in ROS to connect to the current node.

.. code:: shell

    export ROS_IP=[ip_address]

This line sets the environment variable `ROS_IP`, which specifies the IP address of the current node. In this case, the IP address should be set to the IP address of the machine running the current node. This variable is used by other nodes in ROS to connect to the current node.

Environment Loader
------------------

In ROS, the env.sh file is used to set environment variables for a specific workspace. This file is typically located in the devel folder of the workspace, and it is sourced before running any ROS commands in that workspace.

In the case of a slave node in a ROS network, the env.sh file can be used to set the environment variables necessary for the node to communicate with the master node and other nodes in the network.

Here are some common environment variables that can be set in the env.sh file for a slave node:

ROS_MASTER_URI: This variable specifies the URI of the ROS master node. It should be set to the URI of the master node that the slave node will be communicating with. For example:

.. code:: shell

    export ROS_MASTER_URI=http://192.168.0.100:11311

ROS_IP or ROS_HOSTNAME: These variables specify the IP address or hostname of the machine running the slave node. They are used by other nodes in the network to connect to the slave node. For example:

.. code:: shell

    export ROS_IP=192.168.0.101
    export ROS_HOSTNAME=my-slave-machine

ROS_NAMESPACE: This variable specifies the namespace for the node. Namespaces are used to group nodes together and prevent name collisions. For example:


.. code:: shell

    export ROS_NAMESPACE=my_slave_node

By setting these environment variables in the env.sh file, the slave node can properly communicate with the ROS master node and other nodes in the network. It is important to ensure that the values for these variables are correct and consistent across all nodes in the network to avoid communication errors.

.. warning::
    You are specifying the machine's name and password in the launch file, which is not saved because you are giving master, access to your machine.