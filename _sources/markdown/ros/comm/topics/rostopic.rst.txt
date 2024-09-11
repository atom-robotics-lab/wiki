ROS 2 Topic Command
===================

-  `ros2 topic` is a command-line tool for displaying debug information about ROS 2 Topics, including publishers, subscribers, publishing rates, and ROS Messages.

-  Use

.. code:: shell

   ros2 topic --help

to get the help for the `ros2 topic` command.

ros2 topic list
---------------

-  `ros2 topic list` returns a list of all topics currently being subscribed to and published.

-  In one terminal, ensure your ROS 2 environment is sourced and then run:

.. code:: shell

   ros2 topic list

The above will give you a list of the default ROS 2 topics.

-  For this tutorial, we will also use `turtlesim`. Please run in a new terminal:

.. code:: shell

   ros2 run turtlesim turtlesim_node

You will see a small blue box with a turtle inside it.

-  Now, check again the `ros2 topic list` command in another terminal and observe the topics being subscribed to or published.

ros2 topic type, info, and ros2 interface
-----------------------------------------

type
----

Communication on topics happens by sending ROS 2 messages between nodes. To communicate, the publisher and subscriber must use the same message type. You can determine the message type being used on a topic with the `ros2 topic type` command.

.. code:: shell

   ros2 topic type [topic_name]

From the turtlesim node, we know that there are several topics being published/subscribed, such as:

-  `/turtle1/cmd_vel`
-  `/turtle1/pose`
-  `/turtle1/color_sensor`

Let’s check the message type associated with the topic `/turtle1/cmd_vel`. Enter the following command:

.. code:: shell

   ros2 topic type /turtle1/cmd_vel

ros2 interface show
-------------------

-  The message type associated with `/turtle1/cmd_vel` is `geometry_msgs/msg/Twist`. To see the message details, you can use the `ros2 interface show` command:

.. code:: shell

   ros2 interface show geometry_msgs/msg/Twist

-  A message consists of fields and constants. Fields represent the data type, and constants hold predefined values.

-  You will see two fields under `geometry_msgs/msg/Twist`:

   - ``geometry_msgs/Vector3 linear`` : Describes the linear velocities for all three axes.
   - ``geometry_msgs/Vector3 angular`` : Describes the angular velocities for all three axes.

ros2 topic info
---------------

-  This command provides more detail about a topic, including both the message type and the nodes publishing and subscribing to it.

.. code:: shell

   ros2 topic info /turtle1/cmd_vel

ros2 topic pub
--------------

-  `ros2 topic pub` is used to publish data onto a topic currently advertised.

-  Usage:

.. code:: shell

   ros2 topic pub [topic] [msg_type] [args]

-  Let’s move the turtle in the simulator by publishing a command to `/turtle1/cmd_vel`:

.. code:: shell

   ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.5}}"

-  The above command will rotate the turtle clockwise around its z-axis.

-  However, the turtle will only rotate briefly because the command is sent only once. To continuously send the command, use the `--rate` argument.

.. code:: shell

   ros2 topic pub --rate 10 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.5}}"

-  The turtle will now rotate continuously at a rate of 10Hz. You can always get more information about the `pub` command by typing:

.. code:: shell

   ros2 topic pub --help

ros2 topic echo
---------------

-  `ros2 topic echo` shows the data being published on a topic.

-  Usage:

.. code:: shell

   ros2 topic echo [topic]

-  Let’s check the pose information of the turtle in turtlesim, which is published on the `/turtle1/pose` topic. Run:

.. code:: shell

   ros2 topic echo /turtle1/pose

-  You will see the x, y, z, and theta values (pose) of the turtle being published in real time.
