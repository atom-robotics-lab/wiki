Creating a workspace
====================

**Goal:** Create a workspace and learn how to set up an overlay for development and testing.

.. contents:: Contents
   :depth: 2
   :local:

Background
----------

A workspace is a directory containing ROS 2 packages.
Before using ROS 2, it's necessary to source your ROS 2 installation workspace in the terminal you plan to work in.
This makes ROS 2's packages available for you to use in that terminal.



1 Source ROS 2 environment
^^^^^^^^^^^^^^^^^^^^^^^^^^

Your main ROS 2 installation will be your underlay for this tutorial.
(Keep in mind that an underlay does not necessarily have to be the main ROS 2 installation.)

Depending on how you installed ROS 2 (from source or binaries), and which platform you're on, your exact source command will vary:


.. code-block:: console

  source /opt/ros/{DISTRO}/setup.bash


.. _new-directory:

2 Create a new directory
^^^^^^^^^^^^^^^^^^^^^^^^

Best practice is to create a new directory for every new workspace.
The name doesn't matter, but it is helpful to have it indicate the purpose of the workspace.
Let's choose the directory name ``ros2_ws``, for "development workspace":


.. code-block:: console

  mkdir -p ~/ros2_ws/src
  cd ~/ros2_ws/src



Another best practice is to put any packages in your workspace into the ``src`` directory.
The above code creates a ``src`` directory inside ``ros2_ws`` and then navigates into it.


3 Build the workspace with colcon
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

From the root of your workspace (``/ros2_ws``), you can now build your packages using the command:




.. code-block:: console

  colcon build


The console will return the following message:

.. code-block:: console

  Summary: 0 packages finished [0.28s]

.. note::

  Other useful arguments for ``colcon build``:

  * ``--packages-up-to`` builds the package you want, plus all its dependencies, but not the whole workspace (saves time)
  * ``--symlink-install`` saves you from having to rebuild every time you tweak python scripts
  * ``--event-handlers console_direct+`` shows console output while building (can otherwise be found in the ``log`` directory)
  * ``--executor sequential`` processes the packages one by one instead of using parallelism

Once the build is finished, enter the command in the workspace root (``~/ros2_ws``):



.. code-block:: console

  ls

And you will see that colcon has created new directories:

.. code-block:: console

  build  install  log  src

The ``install`` directory is where your workspace's setup files are, which you can use to source your overlay.


4 Source the overlay
^^^^^^^^^^^^^^^^^^^^

Before sourcing the overlay, it is very important that you open a new terminal, separate from the one where you built the workspace.
Sourcing an overlay in the same terminal where you built, or likewise building where an overlay is sourced, may create complex issues.

In the new terminal, source your main ROS 2 environment as the "underlay", so you can build the overlay "on top of" it:



.. code-block:: console

  source /opt/ros/{DISTRO}/setup.bash



Go into the root of your workspace:



.. code-block:: console

  cd ~/ros2_ws


In the root, source your overlay:



.. code-block:: console

  source install/local_setup.bash


.. note::

  Sourcing the ``local_setup`` of the overlay will only add the packages available in the overlay to your environment.
  ``setup`` sources the overlay as well as the underlay it was created in, allowing you to utilize both workspaces.

  So, sourcing your main ROS 2 installation's ``setup`` and then the ``ros2_ws`` overlay's ``local_setup``, like you just did,
  is the same as just sourcing ``ros2_ws``'s ``setup``, because that includes the environment of its underlay.

