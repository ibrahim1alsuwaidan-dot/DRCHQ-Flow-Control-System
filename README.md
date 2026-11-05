# HQ Flow Control System

An automated headcount and occupancy tracking system powered by an ESP32. This system uses dual ultrasonic sensors to detect bidirectional movement (entry and exit) to maintain a real-time count of people inside the HQ. 

It features a local TFT display for immediate visual feedback and hosts an independent captive web server (Access Point mode) to display a live dashboard without requiring an external internet connection.

## Features
* **Directional Tracking:** Uses sequence-based logic with two ultrasonic sensors to determine if a person is entering or exiting.
* **Local TFT Dashboard:** Real-time occupancy display using the `TFT_eSPI` library.
* **Offline Web Server:** The ESP32 broadcasts its own WiFi network (`HQ_Dashboard`). Connecting to it allows users to view the headcount dashboard locally via a web browser.

## Hardware Requirements
* ESP32 Development Board
* 2x HC-SR04 Ultrasonic Sensors (Sensor 1 for Outer side, Sensor 2 for Inner side)
* TFT Display (e.g., ILI9341 or ST7735)
* Jumper wires & Breadboard

## Wiring Guide
| ESP32 Pin | Component       | Pin Connection |
|-----------|-----------------|----------------|
| 3V3 / 5V  | All Sensors/TFT | VCC            |
| GND       | All Sensors/TFT | GND            |
| GPIO 5    | Ultrasonic 1    | TRIG           |
| GPIO 18   | Ultrasonic 1    | ECHO           |
| GPIO 19   | Ultrasonic 2    | TRIG           |
| GPIO 21   | Ultrasonic 2    | ECHO           |
| Hardware SPI | TFT Screen   | SCK, MOSI, CS, DC, RST (Configure in User_Setup.h) |

## Software Setup
1. Install the [TFT_eSPI library](https://github.com/Bodmer/TFT_eSPI) in your Arduino IDE or PlatformIO.
2. Navigate to the library folder and edit `User_Setup.h` to match your specific TFT driver and pinout.
3. Flash the code to the ESP32.
4. Connect your phone or laptop to the WiFi network **HQ_Dashboard** (Password: `admin1234`).
5. Open a browser and navigate to `http://192.168.4.1` to view the live dashboard.
