Installation of virtualenvwrapper, OpenCV and cv_bridge package :
=================================================================

Installation of virtualenvwrapper
---------------------------------

.. code:: shell

   pip install virtualenvwrapper

To open .bashrc
---------------

.. code:: shell

   nano ~/.bashrc

Paste these lines in the .bashrc file which you opened above:
-------------------------------------------------------------

.. code:: bash

   export WORKON_HOME=$HOME/.virtualenvs
   export PROJECT_HOME=$HOME/Devel
   source /usr/local/bin/virtualenvwrapper.sh

To update shell environment
---------------------------

.. code:: bash

   source ~/.bashrc

-  If you face an error here, then reopen the .bashrc file by :

.. code:: bash

   nano ~/.bashrc

Change source from
------------------

.. code:: bash

   source /usr/local/bin/virtualenvwrapper.sh

to
--

.. code:: bash

   source $HOME/.local/bin/virtualenvwrapper.sh

and update shell environment by
-------------------------------

.. code:: bash

   source ~/.bashrc

New virtual environment
=======================

Make a new virtual environment
------------------------------

.. code:: bash

   mkvirtualenv [name of your virtual environment]

To use the new virtual environment
----------------------------------

.. code:: bash

   workon [name of your virtual environment]

To deactivate virtual environment
---------------------------------

.. code:: bash

   deactivate

Your virtual environment is now installed
-----------------------------------------

Installation of opencv
======================

.. code:: bash

   pip install opencv-python

Open Python interpreter in terminal by :
----------------------------------------

.. code:: bash

   python

Import opencv in the above open Python interpreter
--------------------------------------------------

.. code:: python

   import cv2

If your import statement executes error-free, you are good to go
----------------------------------------------------------------

Installation of cv-bridge
=========================

Open your terminal and write :
------------------------------

.. code:: bash

   sudo apt-get install ros-noetic-cv-bridge

To check if cv_bridge is installed
----------------------------------

Note : cv_bridge is a ros package, so make sure you source your ROS before running the command below
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: bash

   rospack find cv_bridge
