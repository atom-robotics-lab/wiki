ROS Topics
==========

-  ROS 2 Topics allow unidirectional communication between ROS 2 Nodes.

-  When using ROS 2 Topics, a ROS Node can act as a **publisher**, **subscriber**, or both.

-  A **ROS Node** acting as a publisher can publish data on a **ROS Topic**, and a **subscriber** ROS Node can subscribe to a **ROS Topic**.

-  Publisher and Subscriber Nodes will exchange **ROS Messages** over a **ROS Topic**.

-  A **ROS Message** is a simple data structure comprising typed fields (integers, floating point numbers, booleans, etc.), so a ROS Message can hold data of various types.

*Consider this analogy* 
-----------------------

-  Let’s say you are subscribed to a newspaper called *The Galactic*, published by a publishing house called OSRF.

-  Every morning your paperboy, Jon Doe, will deliver this newspaper to you.

  ``OSRF <--> ROS 2 Publisher Node``

-  OSRF, acting as the **Publisher Node**, is publishing the newspaper.

  ``You <--> ROS 2 Subscriber Node``

-  You, along with your neighbors who are subscribed to the newspaper, are the **Subscriber Nodes**.

  ``Jon Doe <--> ROS 2 Topic``

-  Jon Doe, the paperboy delivering the newspaper from the publisher to its subscribers, acts as the **ROS 2 Topic**.

  ``The Galactic Newspaper <--> ROS 2 Message``

-  The physical newspaper represents the **ROS 2 Message**.

  ``Sports and Technology Sections of The Galactic <--> Data Fields in ROS 2 Message``

-  The sections of the newspaper are equivalent to the Data Fields defined in the **ROS 2 Message**.
