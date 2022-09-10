Ready to use image for Raspberry Pi
===================================

Custom 64 bit raspbian server image for raspberry pi 4/3b+ with
pre-installed ROS noetic and many other useful packages for ready to use
prototyping

`Download Link <https://drive.google.com/u/0/uc?id=1LYr8p5FBA-MVOaV6yugyCXJ2T71vWfGg&export=download&confirm=t&uuid=e87efbb1-d8e4-4c25-a82e-a93d25260810>`_


The Need
--------

Immagine the time you have completed your simulation and now you are
ready to implement it on your awesome hardare. But to test that
beautiful code you get through the boardem task of preping your sd card
with a fresh flash of raspbian and go through the tedious job of
installing ROS and other packages in it.

So to avoid that we came up with the idea of creatig our own custom
image with pre-installed ROS and many other packages for a user friendly
experiance.

So the next time you mess you mess up something big time, dont worry!
Just get ready with a fresh flash of this image and you are good to go.

Initial Setup
-------------

To get started, download the image file using the link given above.
Alright, once the download is complete, it’s time to flash it on your sd
card. You could do that using various softwares like Balena Etcher,
RUFUS or use the Official Raspberry Pi Imager.

-  **WIFI and SSH**: While working with ROS and robotics related
   projects you will be required to establish a ssh connection with your
   raspberry pi to avoid the hassle of connecting it to a display via
   HDMI. So in order to establish a ssh connection with your laptop both
   the devices needs to be on the same network. To do so, plug in your
   sd card in your computer and open the ``wpa_suppicant.conf`` file in
   a text editor and add your **ssid** and **password** accordingly.
   This will automatically connect your raspberry pi to the network on
   startup.

Ok, Once you pi is on the same network, we need to identify the ip
address of for raspberry pi in order to ssh into it. You could use the
following command to find all devices connected on the network

.. code:: shell

   sudo nmap -sN <IP of your device>/24

Find the IP of your raspberry in the list and ssh into using the command
below.

.. code:: shell

   ssh pi@<IP of your Raspberry Pi>

alright! you’re all set up and good to go.

.. NOTE:: Delault username: **pi** Default password: **raspberry**

Featues and usage
-----------------

-  **ROS**: The image comes with pre-installed ROS neotic and Nav stack
   packages. For installation and more info on ROS please visit our
   Intro to ROS section.

   -  **ROS Master-Slave communication**: ROS Master-Slave communication
      is essential when you are working with computational heavy
      packages which can can create a toll on your raspberry pi. To
      avoid that a Master-Slave communication is established so you can
      run differnet nodes on different devices accordingly. While using
      the above image, the raspberry pi is assumed to be a slave
      considering its master running on your host device (eg: your ROS
      running laptop). In order to do so, open your ``.bashrc`` file in
      your ``/home`` directory and add the following lines in the end.

   .. code:: bash

      export ROS_MASTER_URI=http://localhost:11311/
      export ROS_HOSTNAME=<ROS IP OF YOUR MASTER DEVICE>
      export ROS_IP=<ROS IP OF YOUR MASTER DEVICE>

   Once you are done with that, just save it and close the editor and
   save it. Source the edited bashrc or open a fresh terminal and run
   ``roscore`` and you will see your ROS_MASTER_URI has been changed
   from local host to the IP of your master device.

   Once the master url has been exposed, your raspberry pi can connect
   to your device as a slave. To do so open the ``.bashrc`` file of
   raspberry pi and navigate to the botom. You will find some similar
   lines. Change the IP adress of your devices accordingly and you are
   good to go…

-  **virtualenvwrapper**: virtual enviroment wrapper is a great tool for
   switching between diffenent python enviroments for diffent projects.
   The image comes pre-installed with it and has an existing enviroment
   named **cv** with OpenCV installed created in it. just type the below
   command and you are good to go.

.. code:: shell

   workon cv

For more info and its usage please visit our `Virtual Enviroment
tutorial <./virtualenv.md>`__.

-  **workon_ros**: workon ros is an awsome tool to source and switch
   between different ros workspaces made by Jasmeet Singh. The workspace
   is needed to be created and built in a directory called
   ~/ros_workspace/. Once built, you can directly source the workspace
   using the **workon_ros** command. The image is already set up with
   the tool. To source with noetic workspace just paste the command
   below.

.. code:: shell

   workon_ros noetic

`Github repo for the
project <https://github.com/jasmeet0915/workon_ros>`__. Your inputs are
always welcome.
