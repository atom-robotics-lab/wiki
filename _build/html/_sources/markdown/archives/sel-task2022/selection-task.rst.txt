ROS Selection Task 2022
===================

Hi there, Welcome to the Selection Task.

The TASK provided here is the selection criteria for joining the
**A.T.O.M** society. Those who sucessfully finish the task within the
given time frame will be given a chance to give an interview to become a
member of the **A.T.O.M** society.

This task is not just only test your problem solving skills but see your
diligence to learn new stuff the ablity to get the work done.

.. Note::
   All the resources to complete the said task are provided in
   the ROS section of ATOM WIKI. So make sure to check it out if you are
   new to ROS.

.. seealso::
   The deadline for completing the task: 25th March, 2022 Head to the
   Problem statement section to begin with the task.

Problem Statement
-----------------

-  The objective of the task is to move the turtle inside the turtlesim
   window in a inward or outward spiral motion and to stop it after 4
   turns in order to create a spiral as given in the expected output.

-  To acheive this task you are supposed to create a node named
   /node_turtle_spiral within a python script, node_turtle_spiral.py

.. Note::
      Dont worry if you are new to ROS or Linux(Ubuntu), the task
      is fairly simple and we have provided you with ample resource and
      tutorials in this WIKI to the complete this task so only a strong
      will and a little bit of brains is required to get the work done.
      Also even though this just a weekend task we have provided ample
      amount of time as some of you have your end-term exams(onile though).
      So we think two weeks time is enough so you guys can study for your
      exams freely and manage your time in order to complete the task.


Expected Output
---------------

`output video <https://youtu.be/5snhKotl48k>`__

.. raw:: html

   <iframe width="640" height="480" src="https://www.youtube.com/embed/5snhKotl48k" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen>

.. raw:: html

   </iframe>

Procedure
----------

Follow the instructions given below to get started with the task.

-  First, you will need to create a package named selection_task within
   your ROS workspace. Once your package is created, source and build
   your workspace.
-  Within this package, you should have a scripts folder inside which
   you’ll create a python script, named node_turtle_spiral.py.
-  Fill the script with proper programming ethics. Doing this will help
   us understand your code better and quicker than usual.
-  After completing the python script. Make it executable, if it isn’t
   already. To do that, enter the following code.

.. code:: shell

   cd ~/catkin_ws
   catkin_make
   source devel/setup.bash
   chmod +x ~/catkin_ws/src/selection_task/scripts/node_turtle_spiral.py

-  Before executing make sure that roscore is running along with
   turtlesim_node. You can either run them in separate terminals or
   simply create a selection_task.launch file inside the
   ``~/catkin_ws/src/selection_task/launch/`` folder. Launch file can
   run multiple nodes unlike a python/cpp script. Run the launch file,
   enter, This should run three processes in parallel.

-  roscore

-  turtlesim_node

-  node_turtle_spiral.py

.. seealso:: 
   Please refer to the tutorials and resouces given in the wiki or visit
   the official `ROSWIKI <http://wiki.ros.org/Documentation>`__ if you
   need help with anything regarding ROS.

Hints
-----

-  The turtle needs to move in a inward or outward spiral motion with a
   certain increasing or decreasing radius. This radius should be
   sufficient to fit within the turtlesim window. But making it rotate
   in a circular manner, with only velocities to control is something to
   think about.

-  Use linear velocity as well as angular velocity with some combination
   to get this done.

-  Keep track of the number of circles completed so as to know when to
   stop. You can refer to Overview of rospy for more hint

Submission Instruction
----------------------

For Submissions of your work please refer to the following instructions

-  Video

   -  After completing the task, record a video of your work as shown in
      the expected output in the problem statement page
   -  Once the video is recorded, upload the video to Youtube as an
      unlisted video

-  Code

   -  Once your script is complete, add comments to your code to make it
      more readable.
   -  Create a copy of your script and rename it as task\_.py . Your
      example if your name is ‘Alex’, then rename your script as
      task_alex.py

-  Submissions

   -  Once you have both of the above things ready, submit the YouTube
      link of the video and the script in the google form given below

-  Interview

   -  Once we review your submission, we will be calling you for a
      personal interview based on your work.

`Google Form for Task submission <https://forms.gle/PGfqF2ZmzSH3AY1D7>`__

.. Note::
   Even if you are not able to complete entire the task you
   are requested to make the submission of the work that you have done
   anyway.
