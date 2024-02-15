/*# Gsm_module_Cedat_Open_day
A project for Cedat Open Day*/
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

