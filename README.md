#include "HUSKYLENS.h"
#include "SoftwareSerial.h"
#include <AFMotor.h>
AF_DCMotor motor1(1, MOTOR12_1KHZ);
AF_DCMotor motor2(2, MOTOR12_1KHZ);
AF_DCMotor motor3(3, MOTOR34_1KHZ);
AF_DCMotor motor4(4, MOTOR34_1KHZ);
HUSKYLENS huskylens;
SoftwareSerial mySerial(10, 9); // RX, TX
//HUSKYLENS green line >> Pin 10; blue line >> Pin 11
void printResult(HUSKYLENSResult result);
printResult(result);
int xAxis = result.xCenter;
int yAxis = result.yCenter;
int distance = result.height;
Serial.print("xAxis");
Serial.println(xAxis);
Serial.print("yAxis");
Serial.println(yAxis);
Serial.print("distance");
Serial.println(distance);
if (xAxis < 140) {
motor1.setSpeed(220);
motor1.run(FORWARD);
motor2.setSpeed(220);
motor2.run(BACKWARD);
motor3.setSpeed(220);
motor3.run(FORWARD);
motor4.setSpeed(220);
motor4.run(BACKWARD);
//delay(10);
}else if (xAxis > 200) {
motor1.setSpeed(220);
motor1.run(BACKWARD);
motor2.setSpeed(220);
motor2.run(FORWARD);
motor3.setSpeed(220);
motor3.run(BACKWARD);
motor4.setSpeed(220);
motor4.run(FORWARD);
//delay(10);
}else if (distance < 80) {
motor1.setSpeed(200);
motor1.run(BACKWARD);
motor2.setSpeed(200);
motor2.run(BACKWARD);
motor3.setSpeed(200);
motor3.run(BACKWARD);
motor4.setSpeed(200);
motor4.run(BACKWARD);
//delay(10);}
else if (distance > 110) {
motor1.setSpeed(200);
motor1.run(FORWARD);
motor2.setSpeed(200);
motor2.run(FORWARD);
motor3.setSpeed(200);
motor3.run(FORWARD);
motor4.setSpeed(200);
motor4.run(FORWARD);
//delay(10);}else{
motor1.setSpeed(0);
motor1.run(RELEASE);
motor2.setSpeed(0);
motor2.run(RELEASE);
motor3.setSpeed(0);
motor3.run(RELEASE);
motor4.setSpeed(0);
motor4.run(RELEASE);}
} else {
Serial.println("vision body undetected.");
motor1.setSpeed(0);
motor1.run(RELEASE);
motor2.setSpeed(0);
motor2.run(RELEASE);
motor3.setSpeed(0);
motor3.run(RELEASE);
motor4.setSpeed(0);
motor4.run(RELEASE);
}}}
void printResult(HUSKYLENSResult result){
if (result.command == COMMAND_RETURN_BLOCK){
Serial.println(String()+F("Block:xCenter=")+result.xCenter+F(",yCenter=")+result.yCenter+F(",width=")
+result.width+F(",height=")+result.height+F(",ID=")+result.ID);
}else if (result.command == COMMAND_RETURN_ARROW){
Serial.println(String()+F("Arrow:xOrigin=")+result.xOrigin+F(",yOrigin=")+result.yOrigin+F(",xTarget="
)+result.xTarget+F(",yTarget=")+result.yTarget+F(",ID=")+result.ID);
}
else{
Serial.println("Object unknown!");}}
in your project?
● Are there any specific industries or domains where you believe face tracking could have a
significant impact?
