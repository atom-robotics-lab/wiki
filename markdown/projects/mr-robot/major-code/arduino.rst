Arduino
=======

.. code:: C

    void LpwmCb(const std_msgs::Int32& pwm){

        if(pwm.data == 0) { ledcWrite(ledChannel1, 0); ledcWrite(ledChannel2, 0); }
        if(pwm.data > 0)  { ledcWrite(ledChannel1, abs(pwm.data)); ledcWrite(ledChannel2, 0); }
        if(pwm.data < 0)  { ledcWrite(ledChannel1, 0); ledcWrite(ledChannel2, abs(pwm.data));}
    }

This code defines two callback functions, ``LpwmCb()`` and ``RpwmCb()``, which take a std_msgs::Int32 object as input. The functions control the speed of 2 motors by writing PWM signals using the ledcWrite function.

- The if statements check the value of the input pwm.data and determine which PWM signal to write to each motor. 
- If pwm.data is zero, then both PWM signals for the corresponding motor are set to zero, which stops the motor. 
- If pwm.data is positive, then the first PWM signal is set to the absolute value of pwm.data, which sets the motor to move forward. 
- If pwm.data is negative, then the second PWM signal is set to the absolute value of pwm.data, which sets the motor to move backward.

.. code:: C

    void setup() {

      nh.initNode();
    
      nh.advertise(left_enc_pub);
      nh.advertise(right_enc_pub);
      nh.advertise(left_enc_error);
      nh.advertise(right_enc_error);

      nh.subscribe(Lpwm_sub);
      nh.subscribe(Rpwm_sub);

      ledcSetup(ledChannel1, freq, resolution);
      ledcSetup(ledChannel2, freq, resolution);
      ledcSetup(ledChannel3, freq, resolution);
      ledcSetup(ledChannel4, freq, resolution);

      pinMode(encoderLPin1, INPUT_PULLUP); 
      pinMode(encoderLPin2, INPUT_PULLUP);
      pinMode(encoderRPin1, INPUT_PULLUP); 
      pinMode(encoderRPin2, INPUT_PULLUP);

      pinMode(standby, OUTPUT);
      digitalWrite(standby, HIGH);

      ledcAttachPin(LForward,      ledChannel1);
      ledcAttachPin(LBackward,     ledChannel2);
      ledcAttachPin(RForward,      ledChannel3);
      ledcAttachPin(RBackward,     ledChannel4);

      lastStateL = digitalRead(encoderLPin1);
      lastStateR = digitalRead(encoderRPin1);

      attachInterrupt(digitalPinToInterrupt(encoderLPin1), updateEncoder_L, CHANGE);
      attachInterrupt(digitalPinToInterrupt(encoderLPin2), updateEncoder_L, CHANGE);
    
      attachInterrupt(digitalPinToInterrupt(encoderRPin1), updateEncoder_R, CHANGE);
      attachInterrupt(digitalPinToInterrupt(encoderRPin2), updateEncoder_R, CHANGE);


    }

This code snippet is used to set up the various settings needed for the robot to operate, including the ROS node, PWM signals for the motors, encoder signals for the wheels, and interrupt service routines for updating the encoder counts. 

- The ``nh.initNode()`` function initializes a node in the ROS (Robot Operating System).
- The ``nh.advertise`` functions advertise four topics in the ROS : ``left_enc_pub``, ``right_enc_pub``, ``left_enc_error``, and ``right_enc_error``. These topics are used to publish information about the state of the encoders on the left and right wheels of the robot.
- The ``nh.subscribe` functions subscribe to two topics in the ROS : ``Lpwm_sub`` and ``Rpwm_sub``. These topics are used to receive PWM signals that control the speed and direction of the left and right motors.
- The ``ledcSetup`` functions set up four LEDC (LED Control) channels with the specified frequency and resolution. These channels are used to generate **PWM signals for the left and right motors**.
- The ``pinMode`` functions set the pins used for the encoder signals to input mode with pull-up resistors. These pins are used to read the **signals from the encoders on the left and right wheels** of the robot and also this function sets the **standby** pin to output mode. This pin is used to **enable/disable** the motor driver.
- The ``ledcAttachPin`` functions attach each of the four LEDC channels to a specific pin on the Arduino. These pins are used to **output the PWM signals** to the left and right motors.
- The ``lastStateL`` and ``lastStateR`` variables are initialized with the **initial state** of the encoder signals for the left and right wheels, respectively.
- The ``attachInterrupt`` functions attach two interrupt service routines (``updateEncoder_L`` and ``updateEncoder_R``) to the encoder pins for the left and right wheels. These routines are called whenever the state of the encoder signals changes (i.e., when the wheel rotates). They are used to update the encoder counts and calculate the speed of the wheels.

.. code:: C
    
    void publish_encoder_data()
    {
      encoder_msg_left.data = encoderValue_L;
      left_enc_pub.publish(&encoder_msg_left);

      encoder_msg_right.data = encoderValue_R;
      right_enc_pub.publish(&encoder_msg_right);

        encoder_msg_left_error.data = rpmL_error;
      left_enc_error.publish(&encoder_msg_left_error);

      encoder_msg_right_error.data = rpmR_error;
      right_enc_error.publish(&encoder_msg_right_error);
    }

The function ``publish_encoder_data()`` is used to publish the encoder values and any associated errors to their respective ROS topics.

.. code:: C

    void updateEncoder_L(){

    int LMSB = digitalRead(encoderLPin1); 
    int LLSB = digitalRead(encoderLPin2); //LSB = least significant bit

    int Lencoded = (LMSB << 1) |LLSB; //converting the 2 pin value to single number
    int Lsum  = (lastEncoded_L << 2) | Lencoded; //adding it to the previous encoded value

    if(Lsum == 0b1101 || Lsum == 0b0100 || Lsum == 0b0010 || Lsum == 0b1011) encoderValue_L ++;
    if(Lsum == 0b1110 || Lsum == 0b0111 || Lsum == 0b0001 || Lsum == 0b1000) encoderValue_L --;

    lastEncoded_L = Lencoded; //store this value for next time

    }

- The **Lencoded** value is then combined with the previous encoded value of the left motor using the ``bitwise OR operator (|)`` and **stored in the Lsum variable**.
- The function then **checks the value of Lsum** against a set of four possible values **(0b1101, 0b0100, 0b0010, 0b1011)** and increments the ``encoderValue_L`` variable if it matches any of them. Similarly, if Lsum matches one of the four possible values **(0b1110, 0b0111, 0b0001, 0b1000)**, the function decrements the ``encoderValue_L`` variable.
- Finally, the current encoded value (Lencoded) is stored in the ``lastEncoded_L`` variable for use in the next iteration of the function.