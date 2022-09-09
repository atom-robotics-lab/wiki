# Example 2: Launch turtle in forest

## Aim 

* To write a launch ﬁle to run turtlesim_node node and turtle_teleop_key node present in turtlesim package.
* While launching the turtlesim_node make sure to change the background colour of the simulator from blue to forest green.
* Name the launch ﬁle turtlesim.launch and save it in launch folder inside pkg_ros_basics package.

## Code

turtlesim.launch

```xml
<launch>
<node pkg="turtlesim" type="turtlesim_node" name="node_turtlesim_node">
<param name="/turtlesim_node/background_r" value="34" />
<param name="/turtlesim_node/background_g" value="139" />
<param name="/turtlesim_node/background_b" value="34" />
<param name="/background_r" value="34" />
<param name="/background_g" value="139" />
<param name="/background_b" value="34" />
</node>
<node pkg="turtlesim" type="turtle_teleop_key" name="node_turtle_teleop_key" />
❱
</launch>
```

## Run Command

```shell
roslaunch pkg_ros_basics turtlesim.launch
```
