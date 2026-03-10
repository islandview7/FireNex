
# 🔥 FireNex
## Autonomous Fire Monitoring & Firefighting Robot Platform

<p align="center">
<img src="docs/images/cover.png" width="900">
</p>

<p align="center">
Embedded Robotics · Multi‑Sensor Perception · Autonomous Navigation · Web Telemetry
</p>

<p align="center">

![project](https://img.shields.io/badge/project-robotics-blue)
![platform](https://img.shields.io/badge/platform-STM32%20%2B%20ESP32-green)
![architecture](https://img.shields.io/badge/architecture-modular-orange)
![status](https://img.shields.io/badge/status-active-success)
![license](https://img.shields.io/badge/license-MIT-lightgrey)

</p>

---

# 📖 Project Overview

**FireNex** is an autonomous fire monitoring and firefighting robot platform based on **STM32F103C8T6** and **ESP32**.

The system integrates:

- multi‑sensor fire detection
- autonomous patrol
- target approach
- servo‑driven extinguishing mechanism
- wireless telemetry and web visualization

The robot patrols an environment and continuously monitors fire‑related signals.
When abnormal signals are detected, the robot approaches the fire source and releases an extinguishing device.

Core pipeline:

Perception → Decision → Patrol → Fire Detection → Target Approach → Extinguish → Verify → Feedback

---

# 🌐 Web Monitoring Dashboard

<p align="center">
<img src="docs/images/dashboard-overview.png" width="900">
</p>

---

# 🧠 System Architecture

<p align="center">
<img src="docs/diagrams/system-architecture.png" width="850">
</p>

---

# 🤖 Robot State Machine

<p align="center">
<img src="docs/diagrams/state-machine.svg" width="700">
</p>

1. IDLE — system initialization  
2. PATROL — autonomous monitoring  
3. FIRE_DETECTED — multi‑sensor confirmation  
4. AIM — align robot toward fire source  
5. EXTINGUISH — release extinguishing ball  
6. VERIFY — confirm fire disappears  
7. RETURN — resume patrol  
8. FAILSAFE — emergency stop  

---

# 📊 Realtime Data Flow

<p align="center">
<img src="docs/diagrams/dataflow.svg" width="750">
</p>

Sensors → STM32 Processing → State Machine → ESP32 Telemetry → Web Dashboard

---

# 🧩 Hardware Components

| Module | Model |
|------|------|
MCU | STM32F103C8T6 |
Communication | ESP32 / ESP8266 |
Flame Detection | 4‑channel flame sensor |
Smoke Detection | MQ2 |
Temperature Sensor | DHT11 |
Distance Sensor | HC‑SR04 |
IMU | MPU6050 |
Display | OLED |
Motor Driver | Dual DC motor driver |
Motion Feedback | Wheel encoders |
Extinguishing Actuator | Servo |
Extinguishing Payload | Fire extinguishing ball |

---

# 💻 Firmware Architecture

Driver modules:

OLED · Key · MPU6050 · Motor · PWM · Encoder · Serial · BlueSerial · Flame · Smoke · DHT11 · Ultrasonic · Servo · USART · ADC

Application modules:

app_state_machine  
app_patrol  
app_fire  
app_extinguish  

---

# 📂 Repository Structure

FireNex
│
├── firmware
├── docs
│   ├── images
│   │   ├── cover.png
│   │   └── dashboard-overview.png
│   ├── diagrams
│   │   ├── system-architecture.png
│   │   ├── state-machine.svg
│   │   └── dataflow.svg
│   └── pin-mapping.md
│
├── web_dashboard
└── README.md

---

# 🔧 Pin Mapping

See: docs/pin-mapping.md

---

# 🚀 Future Work

- computer vision fire detection  
- autonomous mapping  
- multi‑robot collaboration  
- cloud monitoring  

---

# 📜 License

MIT License
