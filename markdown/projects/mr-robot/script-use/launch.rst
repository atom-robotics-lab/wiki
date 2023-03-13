Launch files
============

**Their are 2 major launch files that we need to run:**

1. bringup.launch
------------------

This launch file is configuring and launching a set of nodes for a robotic system running on ROS (Robot Operating System).

The nodes launched in this file are:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- **ydlidar_ros/X2L.launch**: Launches the driver for a YDLIDAR X2L lidar sensor.
- **joint_state_publisher**: Publishes joint states for the robot.
- **robot_state_publisher**: Publishes the transform tree for the robot.
- **imu_node.py**: Reads IMU data from an MPU6050 sensor.
- **complementary_filter_node**: Applies a complementary filter to IMU data to obtain orientation.
- **tf_broadcaster_imu.py**: Broadcasts the transform of the IMU sensor.
- **serial_node.py**: Establishes a serial communication link with an ESP8266 board running the firmware for the robot.
- **twist_to_pwm.py**: Converts twist messages into PWM signals to control the motors of the robot.
- **esp_diff_tf.py**: Calculates the odometry and publishes it as a transform.
- **joy_node**: Reads input from a joystick or gamepad.
- **robot_pose_ekf**: Uses sensor data to estimate the pose of the robot using an Extended Kalman Filter.
- **rviz**: Launches the RViz visualization tool to visualize the robot and its environment.

The launch file also sets various parameters and remaps topics to ensure that the nodes communicate correctly with each other.

.. note::
We need to specify machine name (master or slave) before every node on which node will run on **default it will run on master**.



2. X2L.launch
-------------

- This is a ROS launch file that launches the **ydlidar_node** node from the **ydlidar_ros** package on a remote machine with IP address **ip_of_machine** and username **username_of_machine(pi)**.
- The launch file sets several parameters for the LIDAR sensor, such as the **serial port and baudrate** used to communicate with it, the frame ID to use for publishing data, and the angle and range limits of the sensor.