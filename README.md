# Smart-Blind-Stick
const int trigPin = 2; // Trigger pin for ultrasonic sensor
const int echoPin = 3; // Echo pin for ultrasonic sensor
int ledPin = 13;       // LED pin
float duration, distance;

void setup() {
  pinMode(trigPin, OUTPUT); // Set trigPin as OUTPUT
  pinMode(echoPin, INPUT);  // Set echoPin as INPUT
  pinMode(ledPin, OUTPUT);  // Set ledPin as OUTPUT
  Serial.begin(9600);       // Start serial communication
}

void loop() {
  // Trigger the ultrasonic sensor
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Measure the duration of the echo pulse
  duration = pulseIn(echoPin, HIGH);

  // Calculate distance in cm
  distance = (duration * 0.0343) / 2;

  // Print distance
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  // Turn LED on or off based on distance
  if (distance >= 8) {
    Serial.println("NO Object Detected");
    digitalWrite(ledPin, LOW);
  } else {
    Serial.println("YES Object Detected");
    digitalWrite(ledPin, HIGH);
  }

  delay(500); // Wait for 500 ms before next measurement
}






# Ultrasonic Distance Measurement with Arduino

This project demonstrates how to use an **HC-SR04 Ultrasonic Sensor** to measure the distance of an object and control an LED based on the proximity of the object.

## Features
- Measures distance using the speed of sound.
- Displays the distance in centimeters via the Serial Monitor.
- Lights up an LED when an object is closer than 8 cm.

## Components Used
- Arduino Board
- HC-SR04 Ultrasonic Sensor
- LED
- Resistor (for the LED)
- Connecting Wires

## Circuit Diagram
- **Trigger Pin** (HC-SR04) -> Pin 2 (Arduino)
- **Echo Pin** (HC-SR04) -> Pin 3 (Arduino)
- **LED** -> Pin 13 (Arduino)

## How It Works
1. The ultrasonic sensor emits a sound wave.
2. The sound wave reflects off an object and returns to the sensor.
3. The time taken for the echo is measured and converted into distance.
4. If the object is closer than 8 cm, the LED turns on. Otherwise, it stays off.

## Code
The Arduino sketch for this project is included in the repository as `distance_sensor.ino`.

## How to Use
1. Connect the components as per the circuit diagram.
2. Upload the code to the Arduino board.
3. Open the Serial Monitor to see the distance readings.
4. Observe the LED lighting up when the object is closer than 8 cm.

## Applications
- Obstacle detection for robots.
- Proximity alarms.
- Basic distance measurement tools.

## License
This project is open-source and available under the MIT License.
