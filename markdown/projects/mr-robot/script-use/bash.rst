Master Slave Ros Communication
===============================

Introduction
------------

In ROS (Robot Operating System), communication between different nodes (e.g., sensors, controllers, and other agents) is established through the use of a Master-Slave connection. The Master node acts as a central hub that manages the communication between different nodes, while the Slave nodes communicate with each other through the Master node.

The Master node is responsible for keeping track of all available Slave nodes and their published topics. It provides a directory service that allows Slave nodes to discover and communicate with each other. Slave nodes, on the other hand, communicate with the Master node to register their published topics and to subscribe to topics published by other Slave nodes.

The Master-Slave connection in ROS is essential for enabling collaboration and coordination between different nodes. For example, a sensor node publishing data on its published topic can be subscribed to by a controller node, which can then use that data to control a robot or execute specific tasks. Additionally, different Slave nodes can communicate with each other to exchange data or coordinate their actions.

The Master-Slave connection in ROS can be established over various communication protocols such as TCP/IP, UDP, or shared memory. ROS provides a set of standard tools and libraries that allow nodes to communicate with each other seamlessly, regardless of the underlying communication protocol.

In summary, the Master-Slave connection in ROS enables communication between different nodes by establishing a central hub (Master node) that manages the communication between Slave nodes. This connection is crucial for enabling collaboration and coordination between different nodes in ROS and is established over various communication protocols.

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

