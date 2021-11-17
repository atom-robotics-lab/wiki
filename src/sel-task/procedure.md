# Procedure

* First, create a package named  pkg_task0 , within your catkin workspace. Once done, compile and source the packages.
* Within this package, you should have a  scripts  folder inside which you'll create a python script, named  node_turtle_revolve.py.
* Fill the script with proper programming ethics. Doing this will help us understand your code better and quicker than usual.
* After completing the python script. Make it executable, if it isn't already. To do that, enter the following code.

```shell
cd ~/catkin_ws
catkin build
source devel/setup.bash
chmod +x ~/catkin_ws/src/pkg_task0/scripts/node_turtle_revolve.py
```

* Before executing make sure that  roscore  is running along with  turtlesim_node. You can
either run them in separate terminals or simply create a  task0.launch  file inside the
`~/catkin_ws/src/pkg_task0/launch/` folder.
Launch file can run multiple nodes unlike a python/cpp script. Run the launch file, enter, This should run three processes in parallel.

roscore
turtlesim_node
node_turtle_revolve.py