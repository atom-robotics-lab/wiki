# Command: rosnode

* rosnode contains the rosnode command-line tool for displaying debug information about ROS Nodes.

*Note:* For quick information about any command, be that outside of ROS, simply type the
command along with suﬃx --h or -help . This is a widely used concept among other Linux 
Command: rosrun commands for quick references. Here's an example for rosnode --h command

* ## list

rosnode list displays a list of all current nodes.

Let's ﬁgure out what argument the list sub-command needs. In a new terminal run start the
rosmaster:

```shell
roscore
```

And in another terminal, run:

```shell
rosrun rospy_tutorials talker
```

And in another terminal, run:

```shell
rosnode list
```

Now the node named talker (node with word talker in it) will be printed on the terminal.

* ## info

* rosnode info /node_name displays information about a node, including publications and subscriptions.
* Let's ﬁgure out what argument the info sub-command needs. In a new terminal run start the

```shell
rosmaster
```

And in another terminal, run:

```shell
rosrun rospy_tutorials talker
```

And in another terminal, run:

```shell
rosnode info <talker_node>
```
This should give details of the particular node

* ## kill

*IMPORTANT:* rosnode kill is not guaranteed to succeed.

* Let's ﬁgure out what argument the kill sub-command needs. In a new terminal run start the rosmaster:

```shell
roscore
```

* And in another terminal, run:

```shell
rosrun rospy_tutorials talker
```

* And in another terminal, run:

```shell
rosnode kill rosout <talker_node>
```
