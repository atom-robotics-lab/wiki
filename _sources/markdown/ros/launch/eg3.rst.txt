Example 3: Load YAML
====================

Aim
---

-  To write a launch ﬁle to load config_my.yaml present in
   pkg_ros_basics package.
-  Also launch the node_param_get_set.py ROS node after loading the YAML
   ﬁle.

Code
----

load_yaml.launch

.. code:: xml

   <launch>
   <rosparam file ="$(find pkg_ros_basics)/config/config_my.yaml"/>
   <node pkg="pkg_ros_basics" type="node_param_get_set.py" name="node_param_get_set">
   </launch>

Run Command
-----------

.. code:: shell

   roslaunch pkg_ros_basics load_yaml.launch
