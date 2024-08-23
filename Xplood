#include <AFMotor.h>

// Initial motor pins
AF_DCMotor motor1(1, MOTOR12_1KHZ); 
AF_DCMotor motor2(2, MOTOR12_1KHZ); 
AF_DCMotor motor3(3, MOTOR34_1KHZ);
AF_DCMotor motor4(4, MOTOR34_1KHZ);

char command; 

void setup() 
{       
  Serial.begin(9600);  // Set the baud rate to match your Bluetooth module.
}

void loop(){
  if (Serial.available() > 0) { 
    command = Serial.read(); 
    Stop(); // Initialize with motors stopped
    
    switch (command) {
      case 'F':  
        forward();
        break;
      case 'B':  
        back();
        break;
      case 'L':  
        left();
        break;
      case 'R':
        right();
        break;
      case 'S': // Add a case for stopping the car
        Stop();
        break;
      default:
        Stop(); // Stop if command is unknown
        break;
    }
  } 
}

void forward() {
  setMotorSpeedAndDirection(FORWARD);
}

void back() {
  setMotorSpeedAndDirection(BACKWARD);
}

void left() {
  motor1.setSpeed(255); 
  motor1.run(BACKWARD); 
  motor2.setSpeed(255); 
  motor2.run(BACKWARD); 
  motor3.setSpeed(255); 
  motor3.run(FORWARD);  
  motor4.setSpeed(255); 
  motor4.run(FORWARD);  
}

void right() {
  motor1.setSpeed(255); 
  motor1.run(FORWARD); 
  motor2.setSpeed(255); 
  motor2.run(FORWARD); 
  motor3.setSpeed(255); 
  motor3.run(BACKWARD); 
  motor4.setSpeed(255); 
  motor4.run(BACKWARD); 
} 

void Stop() {
  setMotorSpeedAndDirection(RELEASE);
}

void setMotorSpeedAndDirection(uint8_t direction) {
  motor1.setSpeed(255);
  motor1.run(direction);
  motor2.setSpeed(255);
  motor2.run(direction);
  motor3.setSpeed(255);
  motor3.run(direction);
  motor4.setSpeed(255);
  motor4.run(direction);
}
