ROS 2 Installation
================
This section serves as an installation guide for setting up the ``ROS 2 Humble`` on **Linux** operating system.
``ROS 2`` is a widely used framework for devgit@github.com:atom-robotics-lab/wiki.giteloping robotics software.

This guide provides step-by-step instructions for installing ``ROS 2``, allowing developers and enthusiasts to get started
with building robotic applications.

-  This Document assumes that the reader has installed Ubuntu 22.04.
   However, if you haven’t installed Ubuntu 22.04 yet make sure to
   install it before proceeding.
-  There are tons of resources available on the Internet to get this
   done.
-  You can download Ubuntu 22.04 ISO (Desktop Image) ﬁle from
   `here <https://releases.ubuntu.com/jammy/>`__.

ROS 2 Humble Installation
-----------------------

Set locale
----------

Make sure you have a locale which supports ``UTF-8``.
If you are in a minimal environment (such as a docker container), the locale may be something minimal like ``POSIX``.
We test with the following settings. However, it should be fine if you're using a different UTF-8 supported locale.

.. code-block:: bash

   locale  # check for UTF-8

   sudo apt update && sudo apt install locales
   sudo locale-gen en_US en_US.UTF-8
   sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
   export LANG=en_US.UTF-8

   locale  # verify settings

Setup Sources
-------------

You will need to add the ROS 2 apt repository to your system.

First ensure that the `Ubuntu Universe repository <https://help.ubuntu.com/community/Repositories/Ubuntu>`_ is enabled.

.. code-block:: bash

   sudo apt install software-properties-common
   sudo add-apt-repository universe

Now add the ROS 2 GPG key with apt.

.. code-block:: bash

   sudo apt update && sudo apt install curl -y
   sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

Then add the repository to your sources list.

.. code-block:: bash

   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

Install ROS 2 packages
----------------------

Update your apt repository caches after setting up the repositories.

.. code-block:: bash

   sudo apt update

.. include:: _Apt-Upgrade-Admonition.rst

.. warning::

   Due to early updates in Ubuntu 22.04 it is important that ``systemd`` and ``udev``-related packages are updated before installing ROS 2.
   The installation of ROS 2's dependencies on a freshly installed system without upgrading can trigger the **removal of critical system packages**.

   Please refer to `ros2/ros2#1272 <https://github.com/ros2/ros2/issues/1272>`_ and `Launchpad #1974196 <https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1974196>`_ for more information.

Desktop Install (Recommended): ROS, RViz, demos, tutorials.

.. code-block:: bash

   sudo apt install ros-{DISTRO}-desktop

ROS-Base Install (Bare Bones): Communication libraries, message packages, command line tools.
No GUI tools.

.. code-block:: bash

   sudo apt install ros-{DISTRO}-ros-base

Development tools: Compilers and other tools to build ROS packages

.. code-block:: bash

   sudo apt install ros-dev-tools

Environment setup
-----------------

Sourcing the setup script
^^^^^^^^^^^^^^^^^^^^^^^^^

Set up your environment by sourcing the following file.

.. code-block:: bash

   # Replace ".bash" with your shell if you're not using bash
   # Possible values are: setup.bash, setup.sh, setup.zsh
   source /opt/ros/{DISTRO}/setup.bash

Try some examples
-----------------

Talker-listener
^^^^^^^^^^^^^^^

If you installed ``ros-{DISTRO}-desktop`` above you can try some examples.

In one terminal, source the setup file and then run a C++ ``talker``\ :

.. code-block:: bash

   source /opt/ros/{DISTRO}/setup.bash
   ros2 run demo_nodes_cpp talker

In another terminal source the setup file and then run a Python ``listener``\ :

.. code-block:: bash

   source /opt/ros/{DISTRO}/setup.bash
   ros2 run demo_nodes_py listener

You should see the ``talker`` saying that it's ``Publishing`` messages and the ``listener`` saying ``I heard`` those messages.
This verifies both the C++ and Python APIs are working properly.
Hooray!

