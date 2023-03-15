Miscellaneous
=============

ASSIGNING PORT FOR LIDAR AND ESP
--------------------------------

It is crucial to assign ports for LIDAR and ESP because both of them receive random ports in ``ttyUSB`` format.

Use This command to identify port and characters after "usb"

.. code:: python

    dmesg | grep ttyUSB

.. code:: python

    sudo nano /etc/udev/rules.d/10-usb-serial.rules

.. code:: python

    SUBSYSTEM=="tty", KERNELS=="1-1.4", SYMLINK+="ttyUSB_ESP"
    SUBSYSTEM=="tty", KERNELS=="1-1.1", SYMLINK+="ttyUSB_LIDAR"

For loading the new rules:-

.. code:: python

    sudo udevadm trigger

By running the next command in the Terminal, you may verify the new names you just made:-

.. code:: python

    ls -l /dev/ttyUSB*