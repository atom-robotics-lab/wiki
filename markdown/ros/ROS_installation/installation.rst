ROS installation
================

-  This Document assumes that the reader has installed Ubuntu 20.04.
   However, if you haven’t installed Ubuntu 20.04 yet make sure to
   install it before proceeding.
-  There are tons of resources available on the Internet to get this
   done.
-  You can download Ubuntu 20.04 ISO ﬁle from
   `here <https://ubuntu.com/download/desktop>`__.

ROS Noetic Installation
-----------------------

Setup your sources.list
~~~~~~~~~~~~~~~~~~~~~~~

Setup your computer to accept software from packages.ros.org.

.. code:: shell

   sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

Setup your keys
~~~~~~~~~~~~~~~

.. code:: shell

       sudo apt install curl # if you haven't already installed curl

.. code:: shell

       curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

Installation
~~~~~~~~~~~~

-  Update package repositories

.. code:: shell

   sudo apt update

-  Install ROS

.. code:: shell

   sudo apt install ros-noetic-desktop-full

Configuration steps
-------------------

#. Adding environment variables: To Automatically add ROS environment
   variables to your bash session every time a new shell (terminal) is
   launched, enter the following commands (this step is similar as
   adding environmental variable in windows):

.. code:: shell

   echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
   source ~/.bashrc

#. Initialize rosdep: Before you can use many ROS tools, you will need
   to initialize rosdep. rosdep enables you to easily install system
   dependencies for source you want to compile and is required to run
   some core components in ROS.

.. code:: shell

   sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
   sudo rosdep init
   rosdep update

More packages to install
------------------------

-  Catkin tools

.. code:: shell

   sudo apt-get install ros-noetic-catkin python3-catkin-tools

-  std_msg package

.. code:: shell

   sudo apt install ros-noetic-std-msgs

-  turtlesim

.. code:: shell

   sudo apt-get install ros-noetic-ros-tutorials
