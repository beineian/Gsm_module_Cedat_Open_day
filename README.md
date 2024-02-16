
/*
/* # Gsm_module_Cedat_Open_day
  A project for Cedat Open Day
*/





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


