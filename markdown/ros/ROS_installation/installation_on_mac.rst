ROS installation on mac
================

-  This Document assumes that the reader has installed ``anaconda3``
   make sure to install it before proceeding.
-  There are tons of resources available on the Internet to get this
   done.
-  You can visit the `anaconda website <https://docs.anaconda.com/free/anaconda/install/mac-os.html>`__ for more details on anaconda installation.

Setting up ROS environment
-----------------------

Make an environment on your computer named ``ROS``
you can use any name but since we are makeing it to run ros we'll name it  ``ROS``

.. code:: shell

   conda create -n ROS python=3.9

- Now enter your ``ROS`` environment

.. code:: shell

   conda activate ROS

- Now we'll add channels to our environment that is ``conda-forge`` and ``robostack``, we are adding conda forge for the package 

.. code:: shell

   conda config --add channels conda-forge 

.. code:: shell

   conda config --add channels robostack

- Set the ``conda`` channel priority to **strict**

.. code:: shell

   conda config --add channel_priority strict

With this our initial setup is done

Installation 
------------

1. Install ros-noetic into the environment 

.. code:: shell

    conda install ros-noetic-desktop-full

2. Now we'll install compilers for our ``ros``

.. code:: shell

    conda install compilers cmake pkg-config make ninja colcon-common-extensions catkin_tools

With this we are all set.

Testing the installation
------------------------

After installation you are able to run rviz and other ros tools.

In the ``conda`` environment activation is the ``ROS`` activation included. There is no need to add a source command in the ``~/.zshrc``. But there is a catch, that you'll have to run ``conda activate ROS`` command in every new instance of terminal.

First terminal

.. code:: shell

   conda activate ROS
   roscore

Second terminal

.. code:: shell

   conda activate ROS
   rviz

How to install ``ROS`` packages on mac
-----------------------------------------

Though we have installed the ros-noetic-desktop-full --version which comes with common built in packages like rviz, turtlesim and many more. There might be something specific you need so you'll need to search up the packag you're looking for `here <https://robostack.github.io/noetic.html>`__

If you've found what you were looking for then run this command and replace the package name with the one you want to install.

.. code:: shell

   conda install ros-noetic-"package name here"

.. Note::
    #. The ROS commands only work while you are in the ROS environment. 
    #. The packages available are a bit limited.
 
