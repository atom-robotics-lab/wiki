rostopic command
================

-  rostopic contains the rostopic command-line tool for displaying debug
   information about ROS Topics, including publishers, subscribers,
   publishing rate, and ROS Messages.

-  Use

.. code:: shell

   rostopic --h

for getting the rostopic command help.

-  .. rubric:: list
      :name: list

-  rostopic list returns a list of all topics currently subscribed to
   and published.

-  In one terminal run

.. code:: shell

   roscore

-  In the other one, run

.. code:: shell

   rostopic list

The above should give you a list of the default ROS topics

-  For this tutorial, we will also use turtlesim. Please run in a new
   terminal:

.. code:: shell

   rosrun turtlesim turtlesim_node

You will see a small blue box with probably a diﬀerent turtle within it.

-  Now, check again the rostopic list command in another terminal and
   observe the topics being subscribed or published.

-  .. rubric:: type, info and rosmsg
      :name: type-info-and-rosmsg

type
----

Communication on topics happens by sending ROS messages between nodes.
To communicate, the publisher and subscriber must send and receive the
same type of message. This means that a topic type is deﬁned by the
message type published on it. The type of the message sent on a topic
can be determined using rostopic type .

.. code:: shell

   rostopic type [topic_name]

From the previous section, we know that the turtlesim node has 3 topics
being published/subscribed.

-  /turtle1/cmd_vel
-  /turtle1/pose
-  /turtle1/color_sensor

Lets consider the topics /turtle1/cmd_vel . Enter the following command
to get the message type.

.. code:: shell

   rostopic type /turtle1/cmd_vel

rosmsg
------

-  As you can observe the type of message associated with
   /turtle1/cmd_vel is geometry_msgs/Twist . let’s look into more detail
   of te message, using

.. code:: shell

   rosmsg show geometry_msgs/Twist

-  A message consists of two parts, ﬁeld and constant. Simply, ﬁelds is
   the datatype and constants are the representative value From the
   above ﬁgure, you can observe that these ﬁeld and constants are
   displayed twice. However, both of these sections, are separate since
   they have a diﬀerent header or diﬀerent sub-information from the same
   robot. The 2 headers seen are…

-  ``geometry_msgs/Vector3 linear`` : Describes the linear velocities of
   all the 3 axes.

-  ``geometry_msgs/Vector3 angular`` : While this header describes,
   angular velocities of all 3 axes.

-  .. rubric:: info
      :name: info

-  This command provides a little more detail about topics then type
   argument.

.. code:: shell

   rostopic info /turtle1/cmd_vel

-  The output of this command will yield both the message type and the
   nodes which are publishing it or subscribing it.

-  .. rubric:: pub
      :name: pub

   -  ``rostopic pub`` publishes data on to a topic currently
      advertised.
   -  Usage

   .. code:: shell

      rostopic pub [topic] [msg_type] [args]

   -  Lets move the turtle inside the sim window

   \```shell rostopic pub /turtle1/cmd_vel geometry_msgs/Twist “linear:
   x: 0.0 y: 0.0 z: 0.0 angular: x: 0.0 y: 0.0 z: 0.0”

-  Now that we have the complete blank (with all constants as zeros) pub
   command for /turtle1 /cmd_vel , let’s rotate it about its z-axis
   (Yep! the Omega variable).

.. code:: shell

   rostopic pub /turtle1/cmd_vel geometry_msgs/Twist "linear:
   x: 0.0
   y: 0.0
   z: 0.0
   angular:
   x: 0.0
   y: 0.0
   z: 0.5

-  After executing the above command you will see the turtle rotating
   clockwise.

-  However, the turtle only rotated for a while and not continuously.
   This is because our pub command was only sent once. So, to keep the
   turtle rotating we need to keep sending our pub command repeatedly.
   And to do so, we’ll use the -r argument with pub command.

-  The following command is used to publish a steady stream of commands
   at a rate of 10Hz.

.. code:: shell

   rostopic pub -r 10 /turtle1/cmd_vel geometry_msgs/Twist "linear:
   x: 0.0
   y: 0.0
   z: 0.0
   angular:
   x: 0.0
   y: 0.0
   z: 0.5"

-  You can always know more about pub command by simply typing rostopic
   pub –help .

-  .. rubric:: echo
      :name: echo

-  rostopic echo shows the data published on a topic.

-  Usage

.. code:: shell

   rostopic echo [topic]

-  In the earlier section, at the end, we used -r argument to keep it
   rotation at an angular velocity of 0.5 units. But what if the
   velocity is unknown and we need this information as feedback to
   control the motion of turtle???
-  Our desire here is to get the pose information or simply one or all
   of the turtle’s x,y, and z values w.r.t to the world.
-  But let’s see if there is any data being published by the turtlesim
   node in the ﬁrst place. To do so, we’ll use the following command…

.. code:: shell

   rostopic list -p

-  From the -p we know 2 topic is being published

.. code:: shell

   /turtle1/color_sensor
   /turtle1/pose

-  Let’s see more into the /turtle1/pose topic.

-  Luckily the pose information of turtle from the turtlesim is being
   published on the topic /turtle1/pose

-  To display the pose data, enter the following command…

.. code:: shell

   rostopic echo /turtle1/pose