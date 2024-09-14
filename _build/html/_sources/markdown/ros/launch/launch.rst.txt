****************
ROS 2 Launch Files
****************

.. contents:: Table of Contents

-  In the previous sections, you must have noticed that we need to manually run each ROS 2 node and load parameters, which can be a tedious process.
-  ROS 2 Launch files simplify this by allowing us to run multiple nodes, load configuration files, and set parameters using a single command.

Create a ROS 2 Launch file
==========================

ros2 launch Command
-------------------

-  `ros2 launch` is a tool for launching multiple ROS 2 nodes either locally or remotely.
-  It uses `.py` or `.launch.xml` files to define which nodes to run and which parameters to set.

Usage:

.. code:: shell

   ros2 launch <package_name> <launch_file>

-  `<package_name>` is the name of the ROS 2 package.
-  `<launch_file>` is the name of the launch file you want to execute.

Steps to Create a Launch File
-----------------------------

1. After creating a package, create a `launch` folder in your package to store the launch files.

.. code:: shell

   cd ~/ros2_ws/src/<package_name>
   mkdir launch

2. Create a launch file by navigating into the `launch` directory and using a Python file or `.launch.xml` file for launch configuration.

.. code:: shell

   cd launch
   touch <file_name>.launch.py

For example, you can name the launch file `my_launch_file.launch.py`.

Basic Launch File Structure in ROS 2
------------------------------------

1. In ROS 2, launch files can be written in Python or XML. Here's an example of a Python-based launch file structure:

.. code:: python

   from launch import LaunchDescription
   from launch_ros.actions import Node

   def generate_launch_description():
       return LaunchDescription([
           Node(
               package='my_package',
               executable='my_node',
               name='my_node_name',
               output='screen',
           ),
       ])

-  `package`: The package that contains the node.
-  `executable`: The name of the node executable (without extension).
-  `name`: A user-defined name for the node.
-  `output`: Set to `screen` to show output in the terminal.

Steps to Load Configuration Files (YAML) in ROS 2
-------------------------------------------------

You can load YAML files in a ROS 2 launch file using the `launch.actions.SetParameterFile` or `ros2 param` commands.

Here’s an example of loading parameters from a YAML file:

.. code:: python

   from launch import LaunchDescription
   from launch_ros.actions import Node
   from launch.actions import SetParameterFile

   def generate_launch_description():
       return LaunchDescription([
           SetParameterFile(
               node_name='my_node',
               parameter_file='$(find my_package)/config/config.yaml'
           ),
           Node(
               package='my_package',
               executable='my_node',
               name='my_node_name',
               output='screen',
           ),
       ])

Running a Shell Script in a ROS 2 Launch File
---------------------------------------------

You can execute shell scripts within a ROS 2 launch file using the `ExecuteProcess` action.

.. code:: python

   from launch import LaunchDescription
   from launch.actions import ExecuteProcess

   def generate_launch_description():
       return LaunchDescription([
           ExecuteProcess(
               cmd=['bash', '$(find my_package)/scripts/my_script.sh'],
               output='screen'
           )
       ])

Example 1: Launch Two ROS 2 Nodes
=================================

Aim
^^^

-  Launch two ROS 2 nodes: `talker` and `listener` from the `demo_nodes_cpp` and `demo_nodes_py` packages, respectively.

Steps
^^^^^

1. Create a launch file `talker_listener.launch.py` in the `launch` folder of your package.

.. code:: python

   from launch import LaunchDescription
   from launch_ros.actions import Node

   def generate_launch_description():
       return LaunchDescription([
           Node(
               package='demo_nodes_cpp',
               executable='talker',
               name='talker_node',
               output='screen',
           ),
           Node(
               package='demo_nodes_py',
               executable='listener',
               name='listener_node',
               output='screen',
           )
       ])

Run Command
^^^^^^^^^^^

.. code:: shell

   ros2 launch <package_name> talker_listener.launch.py

Example 2: Launch Turtlesim with Custom Background Color
========================================================

Aim
^^^

-  Launch the `turtlesim_node` and `turtle_teleop_key` nodes.
-  Change the background color of the Turtlesim simulator from blue to forest green.

Steps
^^^^^

1. Create a launch file `turtlesim_custom.launch.py` in the `launch` folder of your package.

.. code:: python

   from launch import LaunchDescription
   from launch_ros.actions import Node

   def generate_launch_description():
       return LaunchDescription([
           Node(
               package='turtlesim',
               executable='turtlesim_node',
               name='sim_node',
               output='screen',
               parameters=[{
                   'background_r': 34,
                   'background_g': 139,
                   'background_b': 34,
               }]
           ),
           Node(
               package='turtlesim',
               executable='turtle_teleop_key',
               name='teleop_node',
               output='screen',
           )
       ])

Run Command
^^^^^^^^^^^

.. code:: shell

   ros2 launch <package_name> turtlesim_custom.launch.py

Example 3: Load YAML Configuration
==================================

Aim
^^^

-  Load parameters from `config.yaml` and launch the node `node_param_get_set`.

Steps
^^^^^

1. Create a launch file `load_yaml.launch.py` in the `launch` folder of your package.

.. code:: python

   from launch import LaunchDescription
   from launch.actions import SetParameterFile
   from launch_ros.actions import Node

   def generate_launch_description():
       return LaunchDescription([
           SetParameterFile(
               parameter_file='$(find my_package)/config/config.yaml'
           ),
           Node(
               package='my_package',
               executable='node_param_get_set',
               name='param_node',
               output='screen',
           ),
       ])

Run Command
^^^^^^^^^^^

.. code:: shell

   ros2 launch <package_name> load_yaml.launch.py
