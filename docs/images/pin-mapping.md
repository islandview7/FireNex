# STM32F103C8T6 Pin Mapping

This document is generated from the uploaded pin-definition spreadsheet and is intended as the public pin allocation reference for the FireNex project.

## MCU Package Pin Overview

| Pin No. | Pin Name | Signal Type | Timer |
| --- | --- | --- | --- |
| 1.0 | VBAT |  |  |
| 2.0 | PC13-TAMPER-RTC |  |  |
| 3.0 | PC14-OSC32_IN |  |  |
| 4.0 | PC15-OSC32_OUT |  |  |
| 5.0 | OSC_IN |  |  |
| 6.0 | OSC_OUT |  |  |
| 7.0 | NRST |  |  |
| 8.0 | VSSA |  |  |
| 9.0 | VDDA |  |  |
| 10.0 | PA0-WKUP | TIM2_CH1 | 定时器2 |
| 11.0 | PA1 | TIM2_CH2 |  |
| 12.0 | PA2 | UART2 |  |
| 13.0 | PA3 | UART2 |  |
| 14.0 | PA4 | ADCIN |  |
| 15.0 | PA5 | ADCIN |  |
| 16.0 | PA6 | TIM3 | 定时器3 |
| 17.0 | PA7 | TIM3 |  |
| 18.0 | PB0 | ADCIN |  |
| 19.0 | PB1 | ADCIN |  |
| 20.0 | PB2 |  |  |
| 21.0 | PB10 | I2C2_SCL |  |
| 22.0 | PB11 | I2C2_SDA |  |
| 23.0 | VSS_1 |  |  |
| 24.0 | VDD_1 |  |  |
| 25.0 | PB12 | GPIO |  |
| 26.0 | PB13 | GPIO |  |
| 27.0 | PB14 | GPIO |  |
| 28.0 | PB15 | GPIO |  |
| 29.0 | PA8 | TIM1_CH1 | 定时器1 |
| 30.0 | PA9 |  |  |
| 31.0 | PA10 |  |  |
| 32.0 | PA11 | GPIO |  |
| 33.0 | PA12 | GPIO |  |
| 34.0 | PA13 |  |  |
| 35.0 | VSS_2 |  |  |
| 36.0 | VDD_2 |  |  |
| 37.0 | PA14 |  |  |
| 38.0 | PA15 |  |  |
| 39.0 | PB3 | GPIO |  |
| 40.0 | PB4 |  |  |
| 41.0 | PB5 | GPIO |  |
| 42.0 | PB6 | TIM4_CH1 | 定时器4 |
| 43.0 | PB7 | TIM4_CH2 |  |
| 44.0 | BOOT0 |  |  |
| 45.0 | PB8 | I2C1_SCL |  |
| 46.0 | PB9 | I2C1_SDA |  |
| 47.0 | VSS_3 |  |  |
| 48.0 | VDD_3 |  |  |

## Notes

- Power pins, reset pins, oscillator pins, and reserved pins are kept in the table because they are useful for hardware review and schematic cross-checking.
- Timer-related fields are preserved when they appear in the source spreadsheet.
- Some rows in the original spreadsheet are generic package definitions rather than final project assignments; you can refine this file later into a **project-specific functional mapping table**.

## Recommended Project-Level Functional Mapping

Below is a suggested documentation format you can continue to refine after the final wiring is frozen.

| Function Block | Module | Suggested Interface Type | Notes |
| --- | --- | --- | --- |
| Flame sensing | 4-channel flame sensor | ADC / GPIO | Used for fire direction and confirmation |
| Smoke sensing | MQ2 | ADC / optional digital input | Used for combustion-related abnormality |
| Temperature / humidity | DHT11 | Single-bus GPIO | Environment monitoring |
| Obstacle detection | HC-SR04 | Trigger + Echo GPIO | Patrol obstacle avoidance |
| IMU | MPU6050 | I2C | Attitude / motion reference |
| OLED display | OLED | I2C | Local debug and status visualization |
| Wireless telemetry | ESP32 / ESP8266 | UART | Web-side data upload |
| Debug interface | UART / BlueSerial | UART | Serial debugging |
| Servo actuation | Servo | PWM | Flip-plate extinguishing mechanism |
| Motor drive | DC motor driver | PWM + GPIO | Chassis motion control |
| Encoder feedback | Wheel encoders | Timer / encoder interface | Closed-loop speed control |

## Documentation Suggestion

Once the final wiring is fixed, you can extend this file with a second table like this:

| STM32 Pin | Final Connected Module | Direction | Protocol | Description |
| --- | --- | --- | --- | --- |
| PAx | Flame sensor channel 1 | Input | ADC | Left-side flame sensing |
| PAx | Smoke sensor | Input | ADC | Smoke concentration acquisition |
| PBx | ESP32 TX/RX | TX/RX | UART | Wireless telemetry |
| PBx | Servo | Output | PWM | Extinguishing actuator |
| PBx | OLED SDA/SCL | I/O | I2C | Local display |

This approach keeps the current public document accurate while leaving room for your final hardware freeze.
