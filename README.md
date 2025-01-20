# Robotic-Motion-Control-Arduino-and-L293D-Implementation
DC Motor Control Using L293D Motor Driver

Abstract
This report outlines the design and implementation of a control system for four DC motors using the L293D motor driver. The aim is to execute specific motion sequences, including forward, backward, and directional turns, utilizing Arduino Uno and Adafruit Motor Shield.
________________________________________
Introduction
DC motors are widely used in robotics and automation systems for their simplicity and efficiency. In this project, four DC motors were programmed to perform predefined motion sequences. The project leverages the L293D motor driver and Arduino Uno to achieve precise motor control. The inclusion of a simulation via Tinkercad enhances reproducibility and understanding of the setup.
________________________________________
-	Components Hardware
2.	Arduino Uno: Microcontroller for program execution.
3.	Adafruit Motor Shield: Interface for motor control.
4.	L293D Motor Driver: Dual H-bridge driver for bidirectional motor control.
5.	DC Motors (4): Actuators for motion.
6.	Breadboard: Circuit prototyping.
7.	Wires: Connections between components.
8.	Power Supply: Dedicated source for motors.
 
Figure 1
-	Software
1.	Arduino IDE: Code development and deployment.
2.	Tinkercad: Circuit simulation and design.
________________________________________
Methodology
Circuit Connection
•	The Adafruit Motor Shield was mounted onto the Arduino Uno.
•	DC motors were connected to M1, M2, M3, and M4 ports on the Motor Shield.
•	Power and ground connections were secured for all components.
  Figure 2 shows the actual hardware setup.
Simulation
•	A Tinkercad simulation was created to replicate the physical setup.
 
       Figure 3 presents the circuit schematic designed in Tinkercad.
________________________________________
     Library Installation
To successfully run the program, the Adafruit Motor Shield library must be installed in the Arduino IDE. Follow these steps:
1.	Open the Arduino IDE.
2.	Navigate to Sketch > Include Library > Manage Libraries.
3.	In the Library Manager, search for Adafruit Motor Shield.
4.	Select the library and click Install.
5.	Ensure the library is correctly added by checking for the <AFMotor.h> header file in your code.

Programming
•	The control logic was implemented using the Adafruit Motor Shield library in Arduino IDE.
•	Motors were programmed to: 
o	Move forward for 10 seconds.
o	Move backward for 10 seconds.
o	Alternate between left and right turns for 60 seconds.

Code Implementation
#include <AFMotor.h>

// Define motors
AF_DCMotor motor1(1); // Motor 1 connected to M1
AF_DCMotor motor2(2); // Motor 2 connected to M2
AF_DCMotor motor3(3); // Motor 3 connected to M3
AF_DCMotor motor4(4); // Motor 4 connected to M4

void setup() {
  // Set motor speeds (values between 0 and 255)
  motor1.setSpeed(200);
  motor2.setSpeed(200);
  motor3.setSpeed(200);
  motor4.setSpeed(200);
}

void loop() {
  // 1. Move forward for 10 seconds
  moveForward();
  delay(10000); // 10 seconds

  // 2. Move backward for 10 seconds
  moveBackward();
  delay(10000); // 10 seconds

  // 3. Alternate turning right and left for 60 seconds
  unsigned long startTime = millis(); // Record the start time
  while (millis() - startTime < 60000) { // Continue for 60 seconds
    turnRight(); // Turn right
    delay(10000); // 10 seconds
    turnLeft(); // Turn left
    delay(10000); // 10 seconds
  }
}

// Function to move all motors forward
void moveForward() {
  motor1.run(FORWARD); // Motor 1 forward
  motor2.run(FORWARD); // Motor 2 forward
  motor3.run(FORWARD); // Motor 3 forward
  motor4.run(FORWARD); // Motor 4 forward
}

// Function to move all motors backward
void moveBackward() {
  motor1.run(BACKWARD); // Motor 1 backward
  motor2.run(BACKWARD); // Motor 2 backward
  motor3.run(BACKWARD); // Motor 3 backward
  motor4.run(BACKWARD); // Motor 4 backward
}

// Function to turn the vehicle to the right
void turnRight() {
  motor1.run(FORWARD); // Motor 1 forward
  motor2.run(BACKWARD); // Motor 2 backward
  motor3.run(FORWARD); // Motor 3 forward
  motor4.run(BACKWARD); // Motor 4 backward
}

// Function to turn the vehicle to the left
void turnLeft() {
  motor1.run(BACKWARD); // Motor 1 backward
  motor2.run(FORWARD); // Motor 2 forward
  motor3.run(BACKWARD); // Motor 3 backward
  motor4.run(FORWARD); // Motor 4 forward
}
________________________________________
Results
Upon uploading the program to Arduino Uno:
•	Motors moved forward for 10 seconds.
•	Motors moved backward for 10 seconds.
•	Motors alternated between left and right turns for 60 seconds.
 
Figure 4: Hardware setup.
________________________________________
Discussion
The project demonstrates a practical approach to controlling multiple DC motors using Arduino and L293D. By combining hardware implementation with simulation, the design can be further extended to autonomous robotic systems or smart transportation solutions.
________________________________________


References
Tinkercad circuit simulation: (https://www.tinkercad.com/things/6Px5VhsoiAK/editel)
1.	Additional resources: 
o	YouTube tutorial: DC Motor Control Guide.


