Installation of Virtualenvwrapper, OpenCV and cv_bridge package :
=================================================================

We will go over the steps to install these tools step-by-step :

- Virtualenvwrapper

- OpenCV

- cv_bridge

About Virtualenvwrapper
-----------------------
Virtualenvwrapper is a set of extensions and wrappers for creating, managing and deleting Python virtual environments.
You can read more about it `here <https://pypi.org/project/virtualenvwrapper/>`_

Installation of virtualenvwrapper
---------------------------------

We will use Python's Official package manager, Pip for installing virtualenvwrapper.
Open a terminal and enter the following command :

.. code:: shell

   pip install virtualenvwrapper

Now that we have virtualenvwrapper downloaded and installed, we need to add it's path 
in to bashrc so that your Linux installation will be able to locate it.

The bashrc is a script file containing terminal configurations, commands,
environment variables etc. You can learn more about this `here <https://www.digitalocean.com/community/tutorials/bashrc-file-in-linux#defining-aliases-in-bashrc>`_

Follow the steps given below for the same :

.. code:: shell

   nano ~/.bashrc

- Paste these lines in the .bashrc file which you opened above:

.. code:: bash

   export WORKON_HOME=$HOME/.virtualenvs
   export PROJECT_HOME=$HOME/Devel
   source /usr/local/bin/virtualenvwrapper.sh

Now that we have included the paths in the bashrc, we need to execute the given command to 
refresh the environment variables : 


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

- Again refresh the environment variables by :

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
----------------------
OpenCV (Open Source Computer Vision Library) is an open source computer vision and machine learning software library.
It is one of the most commonly used Computer Vision tool. You can learn more about it `here <https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html>`_

Follow the steps given below to install OpenCV. We will again use pip for downloading and installing OpenCV.

.. code:: bash

   pip install opencv-python

- To test our OpenCV installation, Open Python interpreter in terminal by :


.. code:: bash

   python

- Let's try importing opencv in the above opened Python interpreter


.. code:: python

   import cv2

- If your import statement executes error-free, you are good to go 🎉


Installation of cv-bridge
-------------------------
CvBridge is a ROS library that provides an interface between ROS and OpenCV.
You can learn more about it `here <http://wiki.ros.org/cv_bridge/Tutorials/ConvertingBetweenROSImagesAndOpenCVImagesPython>`_

Follow these steps to install cv_bridge : 

- Open a new terminal and execute the given command


.. code:: bash

   sudo apt-get install ros-noetic-cv-bridge

- Execute the command given below to confirm your cv_bridge installation :

.. code:: shell

   rospack find cv_bridge

.. Note:: cv_bridge is a ros package, so make sure you source your ROS before running the command below.