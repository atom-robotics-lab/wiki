Command: rosrun
===============

rosrun allows you to run an executable in an arbitrary package from
anywhere without having to give its full path or cd/roscd there ﬁrst.

Usage:

.. code:: shell

   rosrun <package> <executable>

``<package>`` is nothing but the package name which you have created
using catkin_create_pkg command or used any other package.

``<executable>`` is the python or cpp ﬁle.

To create an executable python file
-----------------------------------

-  After creating a package, create a folder in the package names as
   scripts folder to store all the python ﬁles in that folder.

.. code:: shell

   cd ~/catkin_ws/src/<package>
   mkdir scripts

-  Here we can create python scripts by running this command by going
   into the scripts directory,

.. code:: shell

   cd scripts
   touch filename.py

-  Now you can edit your python ﬁle and before running you have to make
   it executable by running this command once,

.. code:: shell

   cd ~/catkin_ws/src/<package>/scripts
   chmod +x filename.py

-  Here we can create cpp ﬁles by running this command by going into the
   src directory,

.. code:: shell

   cd src
   touch filename.cpp

Now you can edit your cpp ﬁle , but for making it executable we have to
edit the CMakeLists.txt ﬁle

Add these few lines at the bottom of CMakeLists.txt ﬁle,

.. code:: xml

   add_executable(filename src/filename.cpp)
   target_link_libraries(filename ${catkin_LIBRARIES})

Then run this command,

.. code:: shell

   cd ~/catkin_ws
   catkin build
