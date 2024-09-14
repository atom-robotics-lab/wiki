********
Examples
********

Example #1: ROS 2 Node to Get and Set Parameters
===============================================

Aim
---

To write a ROS 2 Node that reads parameters from a `config.yaml` file, prints them on the console, and modifies the phone number.

Code
----

.. code:: python

   node_param_get_set.py

   #!/usr/bin/env python3
   import rclpy
   from rclpy.node import Node

   class ParamNode(Node):
       def __init__(self):
           super().__init__('node_param_get_set')

           # 1. Read from Parameter Server
           self.get_logger().info("Reading from Parameter Server.")
           
           # Get all the parameters inside 'details'
           # Store the parameters in variables
           param_config_my = self.get_parameters_by_prefix('details')
           first_name = param_config_my['name.first'].value
           last_name = param_config_my['name.last'].value
           address = param_config_my['contact.address'].value
           phone = param_config_my['contact.phone'].value

           # Print the parameters
           self.get_logger().info(f">> First Name: {first_name}")
           self.get_logger().info(f">> Last Name: {last_name}")
           self.get_logger().info(f">> Address: {address}")
           self.get_logger().info(f">> Phone: {phone}")

           # 2. Modify the Phone Number
           self.set_parameters([rclpy.parameter.Parameter('details.contact.phone', rclpy.Parameter.Type.INTEGER, 55555)])
           new_phone = self.get_parameter('details.contact.phone').value
           self.get_logger().info(f">> New Phone: {new_phone}")

   def main(args=None):
       rclpy.init(args=args)
       node = ParamNode()
       rclpy.spin(node)
       rclpy.shutdown()

   if __name__ == '__main__':
       main()

Explanation
-----------

- This ROS 2 node reads parameters from the parameter server, prints them, and modifies the phone number.
- It utilizes the ROS 2 `rclpy` library and leverages the `get_parameters_by_prefix()` function to access nested parameters.
- The parameters include first name, last name, address, and phone number. The node prints these values and updates the phone number to `55555`.
