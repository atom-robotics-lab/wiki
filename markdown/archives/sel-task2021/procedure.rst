Procedure
=========

Follow the instructions given below to get started with the task.

-  First, you will need to create a package named selection_task within
   your ROS workspace. Once your package is created, source and build
   your workspace.
-  Within this package, you should have a ‘scripts’ folder inside which
   you’ll create a python script, named node_turtle_revolve.py.
-  Fill the script with proper programming ethics. Doing this will help
   us understand your code better and quicker than usual.
-  After completing the python script. Make it executable, if it isn’t
   already. To do that, enter the following code.

.. code:: shell

   cd ~/catkin_ws
   catkin build
   source devel/setup.bash
   chmod +x ~/catkin_ws/src/selection_task/scripts/node_turtle_revolve.py

-  Before executing make sure that roscore is running along with
   turtlesim_node. You can either run them in separate terminals or
   simply create a selection_task.launch file inside the
   ``~/catkin_ws/src/selection_task/launch/`` folder. Launch file can
   run multiple nodes unlike a python/cpp script. Run the launch file,
   enter, This should run three processes in parallel.

-  roscore

-  turtlesim_node

-  node_turtle_revolve.py

.. seealso::
   Please refer to the tutorials and resouces given in the wiki or visit
   the official `ROSWIKI <http://wiki.ros.org/Documentation>`__ if you
   need help with anything regarding ROS.
