
/*
/* # Gsm_module_Cedat_Open_day
  A project for Cedat Open Day
*/




/*
#include <SoftwareSerial.h>

// Define the RX and TX pins for SoftwareSerial
const int rxPin = 2;  // Connect SIM800l TX to Arduino D2
const int txPin = 3;  // Connect SIM800l RX to Arduino D3

SoftwareSerial sim800lSerial(rxPin, txPin); // RX, TX

void setup() {
  Serial.begin(9600);
  sim800lSerial.begin(9600);
  delay(1000);

  Serial.println("Initializing GSM module...");
  delay(1000);
  sendATCommand("AT");
  delay(1000);
  sendATCommand("AT+CPIN?");
}

void loop() {
  // Your main code goes here
}

void sendATCommand(String command) {
  sim800lSerial.println(command);
  delay(500);

  while (sim800lSerial.available()) {
    String response = sim800lSerial.readStringUntil('\n');
    Serial.println(response);
  }
}











/*
#include <SoftwareSerial.h>

// Define the RX and TX pins for SoftwareSerial
const int rxPin = 2;  // Connect SIM800l TX to Arduino D2
const int txPin = 3;  // Connect SIM800l RX to Arduino D3

SoftwareSerial sim800lSerial(rxPin, txPin); // RX, TX

void setup() {
  Serial.begin(9600);
  sim800lSerial.begin(9600);
  delay(1000);

  Serial.println("Initializing GSM module...");
  delay(1000);
  sendATCommand("AT");
  delay(1000);
  sendATCommand("AT+CPIN?");

  // Set SMS mode
  sendATCommand("AT+CMGF=1");
}

void loop() {
  // Your main code goes here
  sendSMS("0752132243", "Hello from Arduino!");
  delay(5000);  // Delay to allow time for the SMS to be sent

  checkSMS();
  delay(5000);  // Delay to allow time for the SMS to be received

  makeCall("0752132243");
  delay(10000);  // Delay to allow time for the call
}

void sendATCommand(String command) {
  sim800lSerial.println(command);
  delay(500);

  while (sim800lSerial.available()) {
    String response = sim800lSerial.readStringUntil('\n');
    Serial.println(response);
  }
}

void sendSMS(String phoneNumber, String message) {
  String command = "AT+CMGS=\"" + phoneNumber + "\"";
  sendATCommand(command);
  delay(500);
  sim800lSerial.print(message);
  delay(500);
  sim800lSerial.write(26);  // End the SMS by sending Ctrl+Z
  delay(1000);
}

void checkSMS() {
  sendATCommand("AT+CMGL=\"ALL\"");

  while (sim800lSerial.available()) {
    String response = sim800lSerial.readStringUntil('\n');
    Serial.println(response);
  }
}

void makeCall(String phoneNumber) {
  String command = "ATD" + phoneNumber + ";";
  sendATCommand(command);
}
//*/







#include <SoftwareSerial.h>

// Define the RX and TX pins for SoftwareSerial
const int rxPin = 2;  // Connect SIM800l TX to Arduino D2
const int txPin = 3;  // Connect SIM800l RX to Arduino D3

SoftwareSerial sim800lSerial(rxPin, txPin); // RX, TX

void setup() {
  Serial.begin(9600);
  sim800lSerial.begin(9600);
  delay(1000);

  Serial.println("Initializing GSM module...");
  delay(1000);
  sendATCommand("AT");
  delay(1000);
  sendATCommand("AT+CPIN?");

  // Set SMS mode
  sendATCommand("AT+CMGF=1");
}

void loop() {
  // Your main code goes here
  sendSMS("+256784018481", "Hello from Arduino!");
  delay(5000);  // Delay to allow time for the SMS to be sent

  checkSMS();
  delay(5000);  // Delay to allow time for the SMS to be received

  makeCall("+256784018481");
  delay(10000);  // Delay to allow time for the call
}

void sendATCommand(String command) {
  sim800lSerial.println(command);
  delay(500);

  while (sim800lSerial.available()) {
    String response = sim800lSerial.readStringUntil('\n');
    Serial.println(response);
  }
}

void sendSMS(String phoneNumber, String message) {
  String command = "AT+CMGS=\"" + phoneNumber + "\"";
  sendATCommand(command);
  delay(500);
  sim800lSerial.print(message);
  delay(500);
  sim800lSerial.write(26);  // End the SMS by sending Ctrl+Z
  delay(1000);
}

void checkSMS() {
  sendATCommand("AT+CMGL=\"ALL\"");

  while (sim800lSerial.available()) {
    String response = sim800lSerial.readStringUntil('\n');
    Serial.println(response);
  }
}

void makeCall(String phoneNumber) {
  String command = "ATD" + phoneNumber + ";";
  sendATCommand(command);
}
*/


/*  cynthiaz code
  
// ultrasonic sensor pins
const int trigPin =9;
const int echoPin =10;

// pump pin
const int pumpPin =8;
//distance threshold for activating the pump cm
const int distanceThreshold =10;

void setup() {
  // put your setup code here, to run once:
 Serial.begin(9600);
  
  pinMode(trigPin,OUTPUT);
  pinMode(echoPin,INPUT);
  pinMode(pumpPin,OUTPUT);

digitalWrite(pumpPin,LOW);
}

void loop() {
  // put your main code here, to run repeatedly:
 // Trigger ultrasonic sensor
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Measure the time it takes for the ultrasonic pulse to return
  long duration = pulseIn(echoPin, HIGH);
  
  // Convert the time to distance (cm)
  int distance = duration * 0.034 / 2;
  
  // Print distance to serial monitor
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
  
  // Check if distance is less than threshold
  if (distance < distanceThreshold) {
    // Activate the pump
    digitalWrite(pumpPin, HIGH);
    Serial.println("Pump activated");
  } else {
    // Deactivate the pump
    digitalWrite(pumpPin, LOW);
    Serial.println("Pump deactivated");
  }
  
  // Delay before next measurement
  delay(1000);
}

*/

