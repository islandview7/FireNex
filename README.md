🔥 FireNex
Autonomous Fire Monitoring & Firefighting Robot Platform
<p align="center"> <img src="docs/images/cover.png" width="900"> </p> <p align="center">

Embedded Robotics · Multi-Sensor Perception · Autonomous Navigation · Web Telemetry

</p> <p align="center">










</p>
📖 Project Overview

FireNex is an embedded autonomous firefighting robot platform based on STM32F103C8T6 and ESP32.

The system integrates multiple environmental sensors to detect fire hazards and automatically dispatch a mobile robot to approach the target and trigger a servo-based flip extinguishing mechanism.

The robot continuously patrols the environment, detects abnormal fire signals using multi-sensor fusion, and transmits telemetry data to a web-based monitoring dashboard.

Core pipeline:

Perception → Decision → Navigation → Extinguish → Feedback
🚗 Core Features
🔥 Fire Monitoring

Multi-sensor fire detection including:

Flame sensor array

Smoke sensor (MQ2)

Temperature & humidity sensor (DHT11)

🤖 Autonomous Patrol

The robot performs continuous environment patrol and:

scans surroundings

avoids obstacles

monitors environmental signals

🎯 Target Tracking

When fire is detected:

the robot moves toward the fire source

aligns the body and servo actuator

🧯 Extinguishing Mechanism

Fire suppression is achieved by:

servo-driven flip plate

releasing fire extinguishing ball

🌐 Web Monitoring Platform

Real-time monitoring dashboard provides:

device status

alarm statistics

temperature trends

fire detection alerts

🌐 Web Monitoring Dashboard
<p align="center"> <img src="docs/images/dashboard-overview.png" width="900"> </p>

The web dashboard visualizes telemetry data transmitted by ESP32.

Displayed information includes:

alarm statistics

device online status

temperature trends

smoke index

alert event stream

spatial alert distribution

🧠 System Architecture
<p align="center"> <img src="docs/diagrams/system-architecture.png" width="850"> </p>

The system consists of five subsystems:

Sensor Layer

Environmental perception using:

4× Flame sensors

MQ2 smoke sensor

DHT11 temperature & humidity

HC-SR04 ultrasonic sensor

MPU6050 IMU

Control Layer

Central controller:

STM32F103C8T6

Responsible for:

sensor acquisition

motor control

navigation logic

fire detection algorithm

Communication Layer

Wireless communication module:

ESP32 / ESP8266

Functions:

WiFi telemetry

dashboard data upload

debugging interface

Motion Layer

Robot movement system:

dual DC motors

motor driver

wheel encoders

Extinguishing Layer

Fire suppression mechanism:

servo actuator

flip-plate release

fire extinguishing ball

🤖 Robot State Machine

Recommended control state flow:

IDLE — system startup, module initialization

PATROL — autonomous cruising and environment scanning

FIRE_DETECTED — multi-sensor fire confirmation

AIM — robot aligns body and servo toward fire source

EXTINGUISH — release extinguishing ball

VERIFY — confirm fire signal disappears

RETURN — resume patrol

FAILSAFE — timeout or emergency stop

📊 Real-time Data Flow
Sensors
   ↓
STM32 Control Logic
   ↓
ESP32 Communication
   ↓
Web Dashboard

Telemetry information includes:

temperature

smoke concentration

flame detection

robot position

alarm events

🧩 Hardware Components
Module	Model
MCU	STM32F103C8T6
Communication	ESP32 / ESP8266
Flame Detection	4-channel flame sensor
Smoke Detection	MQ2
Temperature	DHT11
Distance	HC-SR04
IMU	MPU6050
Display	OLED
Motor Driver	Dual DC motor driver
Motion Feedback	Wheel encoders
Extinguishing	Servo + fire extinguishing ball
💻 Firmware Architecture

The firmware is organized in modular layers.

Hardware Drivers
OLED
Key
MPU6050
Motor
PWM
Encoder
Serial
BlueSerial
Flame
Smoke
DHT11
Ultrasonic
Servo
USART
ADC
System Layer
main.c
PID control
interrupt handlers
Application Layer
app_state_machine
app_patrol
app_fire
app_extinguish
📂 Repository Structure
FireNex
│
├── firmware
│   ├── drivers
│   ├── user
│   └── app
│
├── docs
│   ├── images
│   ├── diagrams
│   └── pin-mapping.md
│
├── web_dashboard
│
└── README.md
🔧 Pin Mapping

Detailed MCU pin allocation is provided in:

docs/pin-mapping.md

Includes:

sensor interfaces

communication ports

motor PWM channels

I2C peripherals

debugging interfaces

🚀 Future Work

Planned improvements:

computer vision fire detection

multi-robot coordination

autonomous mapping

cloud monitoring platform

📜 License

MIT License

👨‍💻 Author

FireNex Robotics Project

Embedded Systems · Robotics · IoT
