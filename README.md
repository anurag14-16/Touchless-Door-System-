# Touchless Door System 🚪

An automated touchless door system built using an Arduino Uno, HC-SR04 ultrasonic sensor, servo motor, I2C LCD, and LED indicators — simulated on Wokwi.

---

## Overview

This project simulates a contactless door that automatically opens when a person is detected within 20 cm and closes after 3 seconds of no presence. It is designed to reduce physical contact with door handles — useful in hygiene-sensitive environments like hospitals, labs, or public spaces.

---

## Components Used

| Component | Description |
|---|---|
| Arduino Uno | Main microcontroller |
| HC-SR04 Ultrasonic Sensor | Detects presence within threshold distance |
| Servo Motor | Simulates door open/close mechanism |
| I2C LCD (16x2) | Displays door status messages |
| Green LED | Indicates door is open |
| Red LED | Indicates door is closed |

---

## Circuit Diagram

> Simulation screenshot — see Wokwi link below.

| Pin | Connection |
|---|---|
| D9 | HC-SR04 TRIG |
| D10 | HC-SR04 ECHO |
| D6 | Servo Motor Signal |
| D7 | Green LED |
| D8 | Red LED |
| SDA/SCL | I2C LCD |

---

## Working Principle

1. The HC-SR04 ultrasonic sensor continuously measures distance by sending a sound pulse and timing the echo
2. If a person is detected **within 20 cm**, the system triggers the door to open:
   - Servo rotates to **90°** (open position)
   - Green LED turns ON, Red LED turns OFF
   - LCD displays **"Welcome! / Door Opening.."**
3. A timer resets every time presence is detected — the door stays open as long as someone is near
4. If **no presence is detected for 3 seconds**, the door automatically closes:
   - Servo returns to **0°** (closed position)
   - Red LED turns ON, Green LED turns OFF
   - LCD displays **"Touchless Door / Status: CLOSED"**

---

## Simulation

🔗 [Open in Wokwi](https://wokwi.com/projects/466429926530657281)

---

## Code Highlights

- **`getDistance()`** — triggers the ultrasonic sensor and calculates distance in cm using the pulse duration formula: `distance = duration × 0.034 / 2`
- **`setDoorState(bool open)`** — handles all output states (servo, LEDs, LCD) in one clean function call
- **Non-blocking timeout** — uses `millis()` instead of `delay()` for the 3-second close timer, so detection remains continuous

---

## Features

- Automatic door open/close based on proximity
- 3-second presence timeout before closing
- Dual LED status indicators (green/red)
- I2C LCD with real-time status messages
- Serial monitor output for debugging

---

## Author

Anurag  
Simulated using [Wokwi](https://wokwi.com) on Arduino Uno
