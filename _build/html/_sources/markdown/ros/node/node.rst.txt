*********
ROS 2 Nodes
*********

.. contents:: Table of Contents

-  A **ROS 2 Node** is a piece of software/executable that uses ROS 2 to
   communicate with other ROS 2 nodes.
-  ROS 2 Nodes are the building blocks of any ROS 2 application.
-  For example, in a wall-following robot, one ROS 2 node could retrieve
   distance sensor values while another node controls the robot’s
   motors. These nodes communicate to move the robot.
-  Although it’s possible to write the entire application in a single
   node, having multiple nodes ensures modularity and fault tolerance—
   if one node crashes, it won't crash the entire application.
-  A **ROS 2 package** can contain multiple ROS 2 nodes.
-  ROS 2 Nodes can be written in **Python** or **C++**.

Creating a ROS 2 Node
=====================

Steps to Create a Node in Python
--------------------------------

-  Navigate to your ROS 2 package (for example, ``pkg_ros_basics``):

.. code:: shell

   cd ~/ros2_ws/src/pkg_ros_basics

   OR

.. code:: shell

   ros2 pkg create pkg_ros_basics
   cd ~/ros2_ws/src/pkg_ros_basics

-  Create a folder called ``scripts`` for your Python scripts and navigate into the folder.

.. code:: shell

   mkdir scripts
   cd scripts

-  Create a Python script called ``node_hello_ros.py``.

.. code:: shell

   touch node_hello_ros.py

-  Open the script in a text editor and start editing.

.. code:: shell

   gedit node_hello_ros.py

-  The first line of all Python ROS 2 scripts should be the shebang.

.. code:: shell

   #!/usr/bin/env python3

-  Now write a ROS 2 node that prints "Hello World!" to the console.

.. code:: python

   #!/usr/bin/env python3
   import rclpy
   from rclpy.node import Node

   class HelloWorldNode(Node):
       def __init__(self):
           super().__init__('hello_world_node')
           self.get_logger().info('Hello World!')

   def main(args=None):
       rclpy.init(args=args)
       node = HelloWorldNode()
       rclpy.spin(node)
       rclpy.shutdown()

   if __name__ == '__main__':
       main()

-  Make your node executable.

.. code:: shell

   chmod +x node_hello_ros.py

- To add your newly created script, in CMakeLists.txt file
    - Open CmakeLists.txt in your package
    - add the following piece of code as follows

.. code:: shell

   install(PROGRAMS
       scripts/node_hello_ros.py
       DESTINATION lib/${PROJECT_NAME}
   )




-  Now to run your node:

   -  Open a terminal and run:

.. code:: shell

      ros2 run pkg_ros_basics node_hello_ros.py

Command
=======

Command: ros2 run
-----------------

``ros2 run`` allows you to run an executable in an arbitrary package from
anywhere without having to give its full path or cd there first.

Usage:

.. code:: shell

   ros2 run <package> <executable>

``<package>`` is the name of the package you created using the
``ros2 pkg create`` command.

``<executable>`` is the Python or C++ file you want to run.

To create an executable Python file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

-  After creating a package, create a folder in the package called
   ``scripts`` to store all Python files in that folder.

.. code:: shell

   cd ~/ros2_ws/src/<package>
   mkdir scripts

-  Create Python scripts by running this command in the ``scripts`` directory:

.. code:: shell

   cd scripts
   touch filename.py

-  Edit your Python file, and make it executable before running:

.. code:: shell

   chmod +x filename.py

Command: ros2 node
------------------

-  ``ros2 node`` provides command-line tools for displaying and debugging
   ROS 2 nodes.

-  Use the following command to list all active ROS 2 nodes:

.. code:: shell

   ros2 node list

   This will print the names of all active nodes.

-  To get information about a specific node, including its publications and subscriptions:

.. code:: shell

   ros2 node info <node_name>

-  To kill (terminate) a node:

.. code:: shell

   ros2 node kill <node_name>