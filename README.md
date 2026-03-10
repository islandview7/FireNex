🔥 FireNex
Autonomous Firefighting Robot Platform
<p align="center"> <img src="docs/images/cover.png" width="850"> </p> <p align="center">










</p> <p align="center">

🚒 Autonomous Fire Detection
⚡ Multi-Sensor Fusion
🌐 Real-time Telemetry
🤖 Embedded Robotics Platform

</p>
📖 Project Overview

FireNex is an autonomous firefighting robot platform designed for embedded robotics research and education.

The system integrates:

multi-sensor fire detection

autonomous robot motion

wireless telemetry

web-based monitoring interface

The platform demonstrates a complete cyber-physical system pipeline:

Perception → Decision → Motion → Feedback

Fire detection data are processed by an STM32 real-time controller, transmitted via ESP32 WiFi, and visualized on a web dashboard.

📸 Demo
Robot Platform
<p align="center"> <img src="docs/images/robot.png" width="550"> </p>
Web Monitoring Dashboard
<p align="center"> <img src="docs/images/dashboard.png" width="650"> </p>
✨ Key Features
Feature	Description
🔥 Multi-Sensor Detection	Flame / smoke / temperature sensing
🚗 Autonomous Navigation	Differential drive robot platform
📡 Wireless Communication	ESP32 real-time telemetry
🌐 Web Monitoring	Remote dashboard interface
🧠 Edge Intelligence	Ready for AI expansion
⚙ Embedded Control	STM32 real-time system
🧠 System Architecture
                ┌────────────────────────┐
                │       Web Client       │
                │   Monitoring Interface │
                └───────────┬────────────┘
                            │ WebSocket
                            │
                ┌───────────▼────────────┐
                │         ESP32          │
                │    WiFi Communication  │
                └───────────┬────────────┘
                            │ UART
                            │
                ┌───────────▼────────────┐
                │        STM32 MCU       │
                │ Sensor Fusion + Motion│
                └───────────┬────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
     🔥 Flame            🌫 Smoke             🌡 Temp
     Sensor              Sensor              Sensor
🧩 Hardware Components
Component	Model
Microcontroller	STM32F103C8T6
Communication	ESP32
Flame Sensor	IR Flame Module
Smoke Sensor	MQ-2
Temperature Sensor	DHT11 / DHT22
Motor Driver	L298N
Motors	Dual DC Motors
IMU	MPU6050
Display	OLED
⚙ Firmware Architecture
Module	Description
motor_control.c	Motor PWM control
sensor_manager.c	Sensor acquisition
fire_logic.c	Fire detection algorithm
navigation.c	Robot motion logic
comm_protocol.c	Telemetry protocol
system_state.c	Robot state machine
📂 Repository Structure
FireNex
│
├── firmware
│   ├── Core
│   │   ├── Inc
│   │   └── Src
│   └── Drivers
│
├── hardware
│   ├── schematics
│   └── pcb
│
├── docs
│   ├── images
│   ├── system_architecture.md
│   ├── pin_mapping.md
│   └── communication_protocol.md
│
├── web_dashboard
│
├── tools
│   └── serial_debug
│
└── README.md
🔌 Pin Mapping Example
Device	STM32 Pin
Flame Sensor 1	PB0
Flame Sensor 2	PB1
Smoke Sensor	PA0
Temperature Sensor	PA12
Motor PWM	TIM4
Encoder	TIM3

Detailed wiring:

docs/pin_mapping.md
🚀 Getting Started
1️⃣ Hardware Assembly

Assemble robot chassis

Connect sensors to STM32 ADC pins

Connect ESP32 UART

Install motor driver

2️⃣ Firmware Build

Open project with:

STM32CubeIDE

Compile and flash firmware.

3️⃣ Run Web Dashboard
cd web_dashboard
npm install
npm run dev

Open:

http://localhost:8080
🔥 Fire Detection Logic

Example algorithm:

if (flame_detected && smoke_detected)
{
    fire_level = HIGH;
}
else if (temperature > threshold)
{
    fire_level = MEDIUM;
}
else
{
    fire_level = LOW;
}
📡 Telemetry Protocol

Example serial frame:

$DATA,TEMP=31.5,SMOKE=180,FLAME=1,SPEED=0.23*
📊 Roadmap
Stage	Plan
v1	Basic fire detection
v2	Autonomous patrol
v3	AI fire recognition
v4	Multi-robot collaboration
v5	Cloud monitoring platform
📚 Related Research

Inspired by:

RoboMaster robotics platform

Embedded robotics research

Cyber-physical systems design

🤝 Contributing

Contributions are welcome!

1 Fork repository
2 Create feature branch
3 Commit changes
4 Submit pull request
📜 License

MIT License

👨‍💻 Author

FireNex Robotics Team

Embedded Systems
Robotics
AI + IoT
