ROS installation on mac
================

-  This Document assumes that the reader has installed anaconda3 
   make sure to install it before proceeding.
-  There are tons of resources available on the Internet to get this
   done.
-  You can visit the anaconda website from
   `here <https://docs.anaconda.com/free/anaconda/install/mac-os.html>`__.

ROS Noetic Installation
-----------------------

setup your ROS environment
~~~~~~~~~~~~~~~~~~~~~~~~~~

Make an environment on your computer names ROS
you can use any name but since we are makeing it to run ros we'll name it  ROS

.. code:: shell

   conda create -n ROS python=3.9

- Now enter your ROS environment

.. code:: shell

   conda activate ROS

- Now we'll add channels to our environment that is conda-forge and robostack

.. code:: shell

   conda config --add channels conda-forge 

.. code:: shell

   conda config --add channels robostack

- Set the conda channel priority to strict

.. code:: shell

   conda config --add channel_priority strict

With this our initial setup is done

Installation 
~~~~~~~~~~~~

1. Install ros-noetic into the environment 

.. code:: shell

    conda install ros-noetic-desktop-full

2. Now we'll install compilers for our ros

.. code:: shell

    conda install compilers cmake pkg-config make ninja colcon-common-extensions catkin_tools

With this we are all set

Note- All the ROS commands only work while you are in the ROS environment. 
 
