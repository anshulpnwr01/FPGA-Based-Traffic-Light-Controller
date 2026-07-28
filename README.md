# Arduino Traffic Light Controller

## Overview
This project is a beginner-friendly hardware simulation of a standard intersection traffic light. Built using an Arduino UNO, the system utilizes basic digital outputs and delay timers to cycle through Green, Yellow, and Red states, accurately mimicking real-world traffic signal behavior.

## Circuit Diagram
Below is the wiring diagram for the project, showing how the LEDs and resistors connect to the Arduino.

![Circuit Diagram](WhatsApp%20Image%202026-07-28%20at%207.41.25%20PM%20(1).jpeg)

### Hardware Required
To build this project, you will need the following components:
* **1x** Arduino UNO
* **1x** Breadboard
* **1x** Green LED
* **1x** Yellow LED
* **1x** Red LED
* **3x** Current-limiting Resistors
* Jumper wires

### Wiring Connections
The circuit is wired as follows:
* **Green LED:** Anode connected to Arduino **Digital Pin 1**.
* **Yellow LED:** Anode connected to Arduino **Digital Pin 2**.
* **Red LED:** Anode connected to Arduino **Digital Pin 3**.
* **Ground:** All LED cathodes route through resistors to the shared ground rail on the breadboard, which connects to the Arduino's `GND` pin.

---

## Code Explanation
The logic of the traffic light is straightforward. In the `setup()` function, the three digital pins are configured as outputs. The `loop()` function then controls the sequence in three distinct phases:

1. **Green Phase:** The Green LED is set to `HIGH` (ON), while Yellow and Red are set to `LOW` (OFF). This state holds for 5,000 milliseconds (5 seconds).
2. **Yellow Phase:** The Yellow LED is set to `HIGH`, while Green and Red are set to `LOW`. This state serves as a transition and holds for 2,000 milliseconds (2 seconds).
3. **Red Phase:** The Red LED is set to `HIGH`, while Green and Yellow are set to `LOW`. This state holds for 5,000 milliseconds (5 seconds) before the entire loop restarts.

### Code Snippets
Here are the references for the code structure:

**Setup and Green Light Logic:**
![Code Part 1 - Setup and Green Light](WhatsApp%20Image%202026-07-28%20at%207.41.26%20PM.jpeg)

**Yellow and Red Light Logic:**
![Code Part 2 - Yellow and Red Light](WhatsApp%20Image%202026-07-28%20at%207.41.25%20PM.jpeg)

---

## Full Source Code
For convenience, you can copy the complete Arduino code (`.ino`) below to upload directly to your board:

```cpp
int green = 1;
int yellow = 2;
int red = 3;

void setup() {
  pinMode(green, OUTPUT);
  pinMode(yellow, OUTPUT);
  pinMode(red, OUTPUT);
}

void loop() {
  // Green ON
  digitalWrite(green, HIGH);
  digitalWrite(yellow, LOW);
  digitalWrite(red, LOW);
  delay(5000);

  // Yellow ON
  digitalWrite(green, LOW);
  digitalWrite(yellow, HIGH);
  digitalWrite(red, LOW);
  delay(2000);

  // Red ON
  digitalWrite(green, LOW);
  digitalWrite(yellow, LOW);
  digitalWrite(red, HIGH);
  delay(5000);
}
