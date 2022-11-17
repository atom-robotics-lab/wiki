Create Workspace
================

-  catkin is the oﬃcial build system of ROS and the successor to the
   original ROS build system, rosbuild.
-  catkin combines CMake macros and Python scripts to provide some
   functionality on top of CMake’s normal workﬂow.
-  catkin was designed to be more conventional than rosbuild, allowing
   for better distribution of packages, better cross-compiling support,
   and better portability.

src/
----

-  The src folder contains the source code of catkin packages. This is
   where you can extract/checkout/clone source code for the packages you
   want to build.
-  Each folder within the src folder contains one or more catkin
   packages. This folder should remain unchanged by conﬁguring,
   building, or installing.
-  The root of the src folder contains a symbolic link to catkin’s
   boiler-plate ‘toplevel’ directory. When we execute the catkin_make
   command from the workspace folder, it checks CMakeLists.txt ﬁle. This
   ﬁle is invoked by CMake during the conﬁguration of the catkin
   projects in the workspace. It can be created by calling
   catkin_init_workspace in the src folder inside the src folder and
   builds each package.

build/
------

-  The build folder is where CMake is invoked to build the catkin
   packages in the src folder. CMake and catkin keep their cache
   information and other intermediate ﬁles here.
-  The build folder does not have to be contained within the workspace
   nor does it have to be outside of the src folder, but this is
   recommended

devel/
------

-  The development folder (or devel folder) is where built targets are
   placed before being installed.
-  The way targets are organized in the devel folder is the same as
   their layout when they are installed
-  This provides a useful testing and development environment which does
   not require invoking the installation step.
-  The location of the devel folder is controlled by a catkin speciﬁc
   CMake variable called CATKIN_DEVEL_PREFIX , and it defaults to
   build/devel folder.
-  This is the default behavior because it might be confusing to CMake
   users if they invoked CMake in a build folder and that modiﬁed things
   outside of the current directory.

Creating a catkin workspace
---------------------------

-  Open up the terminal.

-  Create the root workspace directory. You can name your directory
   anything but by ROS convention we will use catkin_ws as the name

.. code:: shell

   cd ~/
   mkdir -p ~/catkin_ws/src/
   cd catkin_ws

-  Initialize the workspace

.. code:: shell

   catkin init

-  Build the workspace

.. code:: shell

   cd  ~/catkin_ws
   catkin_make

-  Now to make your installation deetectable in ROS

.. code:: shell

   source ~/catkin_ws/devel/setup.bash

By doing this , all the packages inside src/ will be visible to ROS

-  The setup.bash will need to be sourced everytime. To not do that ,
   add this to your ~/.bashrc

.. code:: shell

   nano ~/.bashrc
   # Add to the end
   source ~/catkin_ws/devel/setup.bash

Press CTRL+O to save and CTRL+X to save and exit
