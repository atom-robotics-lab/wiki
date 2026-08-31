Electronics Selection Task 2026-2027
====================================


.. note::
   If you don't have hardware available, you can use a simulator such as `Wokwi <https://www.wokwi.com>`__ and `Tinkercad <https://www.tinkercad.com/>`__



This year, we've introduced a four-tiered Electronic Selection Task. Here's a brief summary:

**Challenge Levels**

The electronic selection task is divided into four levels, labeled from Level 0 to Level 3. 
Each level presents its distinct set of challenges. 
Whether you're a novice or an experienced enthusiast, there's something here for everyone.

**Scoring System**

To add an extra layer of excitement, each task within these levels carries a specific point value mentioned alongside 
the problem statement. Your performance will determine your score, and points will be awarded accordingly.

**Qualification Criteria**

To progress to the next stage, which is the interview phase, you must accumulate a minimum of 13 points in total. These 
points will be awarded after evaluating your submissions. Therefore, ensure you put your best foot forward for a chance to advance!

.. note::
   Note: For Level 0, 1,2,and 3 use either Arduino UNO, or esp32 as your
   microcontroller to make the projects.
   Assemble all you components on a breadboard using jumper wires and
   resistors.

Level 0 - Getting Started: 5pts
-------------------------------

Level 0 serves as the foundation and includes following task:-

Task 0A
^^^^^^^
Control the brightness of an LED using a potentiometer.

Task Description
^^^^^^^^^^^^^^^^
* The brightness of the LED should vary smoothly as you rotate the potentiometer.

.. Expected Output
.. ~~~~~~~~~~~~~~~
.. `video link <https://www.youtube.com/shorts/QPaCsf6LROg>`__

.. .. raw:: html

..    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/QPaCsf6LROg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center><br>

Task 0B
^^^^^^^
Play any music theme on a buzzer.
                                                                               
.. Expected Output
.. ~~~~~~~~~~~~~~~
.. `video link <https://www.youtube.com/shorts/QPaCsf6LROg>`__

.. .. raw:: html

..    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/QPaCsf6LROg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center><br>



Level 1 - Challenges: 8pts
--------------------------
Level 1 elevates the complexity with more intricate problems and higher point allocations. Stay tuned for the list of tasks!

Task 1A
^^^^^^^
Light up six LEDs using only three GPIO pins of Arduino/ESP32/Microcontroller. 

Expected Output
~~~~~~~~~~~~~~~
`video link <https://www.youtube.com/watch?v=iGsrljodarg&t=2s>`__

.. raw:: html

   <center><iframe width="560" height="315" src="https://www.youtube.com/embed/iGsrljodarg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center><br>

Task 1B 
^^^^^^^
Control an LED using an Ultrasonic sensor.                                 

Task Description
^^^^^^^^^^^^^^^^
* Take input data from an ultrasonic sensor and convert it into distance (in cm).
* Based on the distance calculated, light up the leds in the following order:
 1. 0-10cm : First LED
 2. 10-20cm: Second LED
 3. 20-30cm: Third LED

.. note::

   You may modify this range as you wish.
   If you are doing it in real life, the ultrasonic sensor may face issues
   in measuring distances less than 3 cm, ignore that error.

Expected Output
~~~~~~~~~~~~~~~
`video link <https://www.youtube.com/shorts/KkR5g6stXqU>`__

.. raw:: html

  <center><iframe width="560" height="315" src="https://youtube.com/embed/KkR5g6stXqU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>


Level 2 - Expert Territory: 8pts
---------------------------------
This level will test even the most seasoned electronic enthusiasts. Prepare for some mind-bending tasks and 
substantial point rewards.

Task 2A
^^^^^^^
Take input from an LDR(Light Dependant Resistor/Photoresistor) and display it on a 16*2 LCD Display.  


Expected Output
~~~~~~~~~~~~~~~
`video link <https://www.youtube.com/watch?v=hIHzK7cB62M>`__

.. raw:: html

  <center><iframe width="560" height="315" src="https://youtube.com/embed/hIHzK7cB62M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

Task 2B
^^^^^^^
* Calculate the distance of an object from an ultrasonic sensor in centimetres and then display it in binary using LEDs.

Task Description
^^^^^^^^^^^^^^^^
* For real life: distance limit: 0-25 cm and No. of LEDs = 5
* For simulation: distance limit: 0-50 cm and No. of LEDs = 6
Ex: if you are using 5 LEDs and the distance reading is “20cm”,
the output should be 10100 i.e. only 1st and 3rd LED should be ON.

Expected Output
~~~~~~~~~~~~~~~
`video link <https://www.youtube.com/watch?v=CAPDpEotP-s>`__

.. raw:: html

  <center><iframe width="560" height="315" src="https://www.youtube.com/embed/CAPDpEotP-s" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

Level 3 - A.T.O.M Special: 13pts
--------------------------------
The ultimate challenge! designed to push the boundaries of your electronics expertise, involving advanced 
problem-solving, precision circuit analysis, and high-reward challenges. 

Task Description(Case-Based):
^^^^^^^^^^^^^^^^
Your exams are right around the corner, but thanks to endless scrolling on
Instagram Reels, your focus and attention span have taken a hit.
To get back on track, you decide to build your own Pomodoro Clock—a
study timer that helps you stay focused for 25 minutes at a stretch, followed by
a short break.

* You have the following components available:
   ESP32/Arduino UNO, 16×2 LCD display, 2 push buttons, 2x10kohm
   resistors, and a 12V DC adapter as your power source.

Directions:
^^^^^^^^^^^
1. The clock should function as a 25-minute study timer with a visible countdown 
   displayed on a screen.
2. After 25 minutes, it should notify the user to take a short break (by displaying a message on the screen).
3. You may implement any number of buttons as needed, but the clock must remain interactive.

.. note::
   If you are making the project in a simulation platform, do not worry
   about the power supply, the platform takes care of that for you.
   But if you are building it in real life… either you use any safe power source
   like 9v battery, a power bank, or simply power by laptop/PC.
   Or you design the PCB listed in the last step.

PCB Designing(Optional Task):
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Since your adapter provides 12V DC, you need to design a power supply
Design a PCB for this mini project powered by an external 12V DC adapter.
The board should also convert input voltage to: 
1. 9 volts 
2. 5 volts(Hint: Try LM2596)

.. note::
   Evaluation for this level will primarily focus on your creativity and design efficiency.

.. Warning::
   The **Deadline** for completing the task: **26th September, 2025**


Head over to `Submissions <https://atom-robotics-lab.github.io/wiki/markdown/selectiontask25/04_submissions.html>`__ to submit your work 
