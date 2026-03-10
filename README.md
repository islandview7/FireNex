# 🔥 FireNex
## Autonomous Firefighting Robot Platform

<p align="center">
  <img src="docs/images/cover.svg" alt="FireNex cover" width="100%" />
</p>

<p align="center">
  <a href="#-overview"><img src="https://img.shields.io/badge/project-robotics-blueviolet" alt="project"></a>
  <a href="#-hardware-platform"><img src="https://img.shields.io/badge/platform-STM32%20%2B%20ESP32-2563eb" alt="platform"></a>
  <a href="#-repository-structure"><img src="https://img.shields.io/badge/architecture-modular-059669" alt="architecture"></a>
  <a href="#-development-roadmap"><img src="https://img.shields.io/badge/status-active-orange" alt="status"></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/license-MIT-e5e7eb" alt="license"></a>
</p>

<p align="center">
  <strong>Perception → Decision → Motion → Feedback</strong>
</p>

<p align="center">
  Multi-sensor fire detection · real-time telemetry · embedded state machine · web-based monitoring
</p>

---

## ✨ Why this repository looks like a real robotics lab project

FireNex is positioned as an **embedded robotics platform**, not just a course demo.  
The repository is organized to make the project easy to **understand, reproduce, extend, and showcase**.

It is built around four core ideas:

- **Perception**: flame, smoke, temperature, distance, and environment sensing
- **Decision**: threshold logic, sensor fusion, patrol strategy, and robot state machine
- **Action**: motor control, obstacle avoidance, aiming, and extinguishing interface
- **Feedback**: OLED debugging, serial protocol, ESP32 telemetry, and browser dashboard

---

## 📖 Overview

**FireNex** is an autonomous firefighting robot platform based on **STM32 + ESP32**.
It combines:

- flame sensing
- smoke sensing
- temperature / humidity sensing
- obstacle distance sensing
- differential-drive motion control
- wireless telemetry
- web dashboard visualization

The project is suitable for:

- electronic design competitions
- embedded systems courses
- robotics club recruitment
- GitHub portfolio building
- future AI / computer vision expansion

---

## 🧠 Core Highlights

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>🔥 Perception</h3>
      <ul>
        <li>Flame array direction sensing</li>
        <li>Smoke threshold detection</li>
        <li>Temperature / humidity monitoring</li>
        <li>Obstacle distance feedback</li>
      </ul>
    </td>
    <td width="33%" valign="top">
      <h3>🤖 Control</h3>
      <ul>
        <li>Finite-state patrol logic</li>
        <li>Differential motion control</li>
        <li>Approach / verify / recover workflow</li>
        <li>Real-time embedded response</li>
      </ul>
    </td>
    <td width="33%" valign="top">
      <h3>🌐 Telemetry</h3>
      <ul>
        <li>UART link to ESP32</li>
        <li>WiFi upload to dashboard</li>
        <li>Structured data frames</li>
        <li>Live status visualization</li>
      </ul>
    </td>
  </tr>
</table>

---

## 🏗️ System Architecture

<p align="center">
  <img src="docs/diagrams/system-architecture.svg" alt="System architecture" width="100%" />
</p>

### Architecture notes

- **STM32** is the real-time control center.
- **ESP32** acts as the wireless communication bridge.
- Sensor data are sampled, fused, and converted into robot decisions.
- Local debugging runs through OLED / serial, while remote data go to the browser dashboard.

---

## 🔄 Robot State Machine

<p align="center">
  <img src="docs/diagrams/state-machine.svg" width="600" >
</p>

### Recommended state flow

1. **IDLE** — power-on, module initialization, threshold loading  
2. **PATROL** — regular cruise, obstacle check, environment scan  
3. **FIRE DETECTED** — multi-sensor confirmation and target locking  
4. **AIM** — align body / servo / extinguisher toward target  
5. **EXTINGUISH** — trigger fan, pump, flip plate, or other module  
6. **VERIFY** — confirm fire signal disappears  
7. **RETURN** — resume patrol or reset system status  
8. **FAIL** — timeout / exception / emergency stop branch

---

## 📊 Realtime Data Flow

<p align="center">
  <img src="docs/diagrams/dataflow.svg" alt="Realtime data flow" width="100%" />
</p>

### Typical telemetry fields

| Field | Meaning |
|---|---|
| `flame_left` | Left flame sensor intensity |
| `flame_mid` | Center flame sensor intensity |
| `flame_right` | Right flame sensor intensity |
| `smoke` | MQ-2 analog value |
| `temp` | Temperature value |
| `hum` | Humidity value |
| `distance` | Obstacle distance in cm |
| `car_mode` | Current robot state |
| `pwm_left` | Left motor PWM |
| `pwm_right` | Right motor PWM |

---

## 🧰 Hardware Platform

| Category | Suggested module |
|---|---|
| MCU | STM32F103C8T6 |
| Communication | ESP32 / ESP32-CAM |
| Flame sensing | 2–3 channel flame sensor array |
| Smoke sensing | MQ-2 |
| Temperature / humidity | DHT11 or DHT22 |
| Distance sensing | HC-SR04 or US-100 |
| Motor driver | TB6612 / L298N |
| Motion | Differential-drive chassis |
| Display | 0.96" OLED |
| Extinguishing module | Fan / pump / flip-plate / servo-driven module |

---

## 🧱 Firmware Design

| File / module | Responsibility |
|---|---|
| `sensor_manager.c` | Sample all sensors and normalize raw values |
| `fire_logic.c` | Fire confirmation logic and threshold policy |
| `navigation.c` | Patrol, approach, turning, obstacle response |
| `motor_control.c` | PWM control and drive abstraction |
| `comm_protocol.c` | UART frame packaging / parsing |
| `system_state.c` | Top-level finite-state machine |
| `debug_view.c` | OLED / serial debug output |

### Suggested firmware loop

```c
while (1)
{
    SensorManager_Update();
    FireLogic_Update();
    Navigation_Update();
    CommProtocol_SendTelemetry();
    DebugView_Render();
}
```

---

## 📂 Repository Structure

```text
FireNex/
├── README.md
├── LICENSE
├── firmware/
│   ├── Core/
│   │   ├── Inc/
│   │   └── Src/
│   ├── Drivers/
│   └── Middlewares/
├── hardware/
│   ├── schematics/
│   ├── wiring/
│   └── mechanical/
├── docs/
│   ├── diagrams/
│   │   ├── system-architecture.svg
│   │   ├── state-machine.svg
│   │   └── dataflow.svg
│   ├── images/
│   │   └── cover.svg
│   ├── pin-mapping.md
│   ├── protocol.md
│   ├── bringup-checklist.md
│   └── testing-plan.md
├── web_dashboard/
│   ├── src/
│   ├── public/
│   └── package.json
└── tools/
    ├── serial_debug/
    └── data_logger/
```

---

## 🚀 Quick Start

### 1. Clone the repository

```bash
git clone https://github.com/your-name/FireNex.git
cd FireNex
```

### 2. Build the STM32 firmware

- Open the project in **STM32CubeIDE** or your preferred toolchain.
- Configure pin mapping according to `docs/pin-mapping.md`.
- Adjust thresholds in `app_config.h`.
- Flash the board and verify sensor readings through serial / OLED.

### 3. Start the web dashboard

```bash
cd web_dashboard
npm install
npm run dev
```

### 4. Connect ESP32 telemetry

- Forward UART data from STM32 to ESP32
- Parse structured frames
- Push updates to the front-end dashboard through WebSocket or HTTP

---

## 🧪 Bring-up Checklist

Use this checklist before the first full robot run:

- [ ] STM32 minimum system boots correctly
- [ ] Motor driver direction and PWM verified
- [ ] Flame sensor values readable and stable
- [ ] Smoke sensor preheated and calibrated
- [ ] DHT data valid and refreshed normally
- [ ] Ultrasonic distance reading stable
- [ ] OLED displays core status info
- [ ] ESP32 receives and forwards serial frames
- [ ] Dashboard shows live telemetry
- [ ] Fire-detection state transitions work as expected

---

## 📸 What to replace with your own real content

This polished template is designed so you can swap in real project material later.

### Replace these first

- `docs/images/cover.svg` → your real robot hero image or a real photo montage
- add `docs/images/robot.jpg` → your chassis photo
- add `docs/images/dashboard.png` → your browser dashboard screenshot
- add `docs/images/demo.gif` → your motion / detection demonstration
- update `docs/pin-mapping.md` → actual pin assignment
- update `docs/protocol.md` → your real serial frame format

### Replace these next

- sensor thresholds
- extinguishing strategy description
- actual video links
- real system performance metrics

---

## 🧭 Development Roadmap

| Version | Goal |
|---|---|
| `v1` | Sensor bring-up + basic telemetry |
| `v2` | Patrol state machine + obstacle avoidance |
| `v3` | Fire approach + extinguishing interface |
| `v4` | Web dashboard + remote alerts |
| `v5` | AI vision / camera / multi-robot expansion |

---

## 📈 What makes this repo more star-worthy

To make the project look and feel like a serious open-source robotics repository, add these next:

- a **30–60 second demo video** at the top of the README
- a **real robot photo** immediately below the cover image
- a **step-by-step build tutorial** in `docs/`
- a **competition-inspired testing plan**
- a **short reproducible hardware BOM**
- polished **GitHub Topics** such as:
  - `robotics`
  - `embedded`
  - `stm32`
  - `esp32`
  - `autonomous-robot`
  - `iot`
  - `fire-robot`

---

## 🤝 Contributing

Contributions are welcome.

Recommended workflow:

1. Fork the repository  
2. Create a feature branch  
3. Commit clear changes  
4. Open a pull request  
5. Add screenshots or logs if the change affects behavior  

---

## 📜 License

This project is released under the **MIT License**.

---

## 👨‍💻 Repository Description

> An autonomous firefighting robot platform based on STM32 and ESP32, featuring multi-sensor fire detection, real-time telemetry, and web-based monitoring.

---

## 🏷️ Suggested GitHub Topics

```text
robotics
embedded
stm32
esp32
autonomous-robot
iot
fire-robot
sensor-fusion
web-dashboard
```

---

## ❤️ Acknowledgement

Designed as a polished robotics-style open-source template for embedded fire-response vehicles, engineering competitions, and portfolio-grade project presentation.
