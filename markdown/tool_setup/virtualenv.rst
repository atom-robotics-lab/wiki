.. role:: python(code)
   :language: python

======================================
Installation of Computer Vision tools
======================================

These are some of the most commonly used Computer Vision tools in Robotics :


virtualenvwrapper
=================

Virtualenvwrapper is a set of extensions and wrappers used for creating, managing and deleting Python virtual environments using
the terminal. Virtual environments are isolated Python installations that help in keeping dependencies required by different 
projects seperated. They also help in keeping a track of the dependencies or packages required by a project during deployement.

You can read more about it `here <https://pypi.org/project/virtualenvwrapper/>`_

OpenCV
=======

OpenCV (Open Source Computer Vision Library) is an open source Computer Vision and Machine Learning software library, originally
developed in C++. It is one of the most commonly used Computer Vision tool nowadays, with client libraries available in
popular languages like Python, Java, MATLAB etc.

You can learn more about it `here <https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html>`_


cv_bridge
==========

The cv_bridge packages contains the :python:`CvBridge` class which provides an interface between ROS and OpenCV. It helps in conversion from ROS Image messages
to OpenCV images and vice-versa.
You can learn more about it `here <http://wiki.ros.org/cv_bridge/Tutorials/ConvertingBetweenROSImagesAndOpenCVImagesPython>`_

Now let's go over the instructions to install these tools one-by-one :


Installation of virtualenvwrapper
==================================


We will use Python's Official package manager, :python:`pip` for installing virtualenvwrapper.
Open a terminal and enter the following command :

.. code:: shell

   pip install virtualenvwrapper

Now that we have virtualenvwrapper downloaded and installed, we need to add it's path 
in the .bashrc file so that your Linux installation will be able to locate it.

The .bashrc file contains terminal configurations, commands,
environment variables etc. You can learn more about this `here <https://www.digitalocean.com/community/tutorials/bashrc-file-in-linux#defining-aliases-in-bashrc>`_

Follow the steps given below for the same :

.. code:: shell

   nano ~/.bashrc

- Paste these lines in the .bashrc file which you opened above:

.. code:: bash

   export WORKON_HOME=$HOME/.virtualenvs
   export PROJECT_HOME=$HOME/Devel
   source /usr/local/bin/virtualenvwrapper.sh

Now that we have included the paths in the .bashrc file, we need to execute the given command to 
load the new environment variables : 


.. code:: bash

   source ~/.bashrc

-  If you face an error here, then reopen the .bashrc file by :

.. code:: bash

   nano ~/.bashrc

- Now change the source  : 


.. code:: bash

   source /usr/local/bin/virtualenvwrapper.sh

- to : 


.. code:: bash

   source $HOME/.local/bin/virtualenvwrapper.sh

- Again try loading the new environment variables by :

.. code:: bash

   source ~/.bashrc

Creating a New Virtual Environment
-----------------------

Now that we have virtualenvwrapper locked and loaded, let's create a new virtual environment.


- The command given below will be used to create a new virtual environment : 


.. code:: bash

   mkvirtualenv [name of your virtual environment]

- To use the new virtual environment


.. code:: bash

   workon [name of your virtual environment]

- To deactivate virtual environment


.. code:: bash

   deactivate


Installation of OpenCV
======================

Follow the steps given below to install OpenCV. We will again use pip for downloading and installing OpenCV.

.. code:: bash

   pip install opencv-python

- To test our OpenCV installation, Open Python interpreter in terminal by :


.. code:: bash

   python

- Let's try importing OpenCV in the above opened Python interpreter


.. code:: python

   import cv2

- If your import statement executes error-free, you are good to go !!

Installation of cv_bridge
==========================

Follow these steps to install cv_bridge : 

- Open a new terminal and execute the given command

.. code:: bash

   sudo apt-get install ros-noetic-cv-bridge

- Execute the command given below to confirm your cv_bridge installation :

.. code:: shell

   rospack find cv_bridge

.. Note:: cv_bridge is a ros package, so make sure you source your ROS installation before running the command below.