<p align="center">
  <img src="./assets/profile-banner.svg" alt="Park Gitae — Embedded Firmware Engineer" width="100%">
</p>

<div align="center">

### STM32 Firmware · FreeRTOS · CAN

센서 데이터를 안정적으로 수집하고,<br>
**Task · FSM · 통신 구조를 통해 실제 제어 동작으로 연결하는 임베디드 펌웨어 엔지니어 박기태입니다.**

<a href="mailto:pkikit95@gmail.com"><img src="https://img.shields.io/badge/Email-pkikit95%40gmail.com-0F766E?style=flat-square&logo=gmail&logoColor=white" alt="Email"></a>
<a href="https://github.com/pkt-gif"><img src="https://img.shields.io/badge/GitHub-pkt--gif-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub"></a>

`SENSE` → `DECIDE` → `COMMUNICATE` → `CONTROL` → `VERIFY`

</div>

---

## Engineering Focus

| MCU FIRMWARE | REAL-TIME & I/O | SYSTEM EXTENSION |
|:---:|:---:|:---:|
| `C` `STM32F4`<br>`HAL` `FSM` | `FreeRTOS` `Task/Mutex`<br>`CAN` `UART` `I²C` `PWM` | `Edge AI`<br>`FPGA SoC` |

> 상태와 메시지의 경계를 먼저 정의하고, 센서–판단–구동의 흐름을 실제 하드웨어에서 검증합니다.

---

## Built Systems

| **01 · [Object-Detecting Taxi](https://github.com/pkt-gif/object-detecting-autonomous-taxi)**<br><sub>FIRMWARE + EDGE AI · TEAM</sub> | **02 · [FreeRTOS Robotaxi](https://github.com/pkt-gif/robotaxi)**<br><sub>REAL-TIME FIRMWARE · SOLO</sub> |
|:---|:---|
| [![Object-detecting taxi demo](https://img.youtube.com/vi/wJaPBZJurDA/hqdefault.jpg)](https://www.youtube.com/watch?v=wJaPBZJurDA) | [![FreeRTOS robotaxi demo](https://img.youtube.com/vi/1cFvFcStp3M/hqdefault.jpg)](https://www.youtube.com/shorts/1cFvFcStp3M) |
| **FLOW**<br>`YOLO/NCNN + Ultrasonic` → `Drive FSM` → `STOP / SLOW / GO` | **FLOW**<br>`SensorTask` → `Mutex` → `DriveTask` |
| **MY PART**<br>`Architecture` · `6-class Data` · `Sensor Fusion` | **BUILD**<br>`3 Tasks` · `P Control` · `AUTO / MANUAL` |
| `STM32F446RE` `FreeRTOS` `CAN` `NCNN` | `STM32F411RE` `FreeRTOS` `UART` `PWM` |
| [Repository ↗](https://github.com/pkt-gif/object-detecting-autonomous-taxi) · [Demo ▶](https://www.youtube.com/watch?v=wJaPBZJurDA) | [Repository ↗](https://github.com/pkt-gif/robotaxi) · [Demo ▶](https://www.youtube.com/shorts/1cFvFcStp3M) · [Autonomous ▶](https://www.youtube.com/shorts/8N2YOQ3bM_4) |

| **03 · [STM32 Lift Controller](https://github.com/pkt-gif/stm32-elevator)**<br><sub>MCU CONTROL · TEAM</sub> | **04 · [Smart Fish Tank](https://github.com/pkt-gif/Smart-fish-tank)**<br><sub>EMBEDDED SENSING · TEAM</sub> |
|:---|:---|
| [![STM32 lift controller demo](https://img.youtube.com/vi/AVxfVoIqJPs/hqdefault.jpg)](https://www.youtube.com/watch?v=AVxfVoIqJPs) | [![Smart fish tank demo](https://img.youtube.com/vi/u2zzdcHJl2s/hqdefault.jpg)](https://www.youtube.com/watch?v=u2zzdcHJl2s) |
| **FLOW**<br>`Keypad + Limit` → `Control FSM` → `Lift / Door` | **FLOW**<br>`LED ON/OFF ADC` → `Difference` → `Relative Turbidity` |
| **MY PART**<br>`Motion Control` · `Safety Limit` · `LED/Buzzer` | **MY PART**<br>`ADC Measurement` · `3-Level Decision` · `Status Display` |
| `STM32F411RE` `HAL` `UART/I²C` `Stepper` | `ATmega128A` `ADC` `I²C` `RGB LED` |
| [Repository ↗](https://github.com/pkt-gif/stm32-elevator) · [Demo ▶](https://www.youtube.com/watch?v=AVxfVoIqJPs) | [Repository ↗](https://github.com/pkt-gif/Smart-fish-tank) · [Demo ▶](https://www.youtube.com/watch?v=u2zzdcHJl2s) |

| **05 · [AXI4-Lite Vending Machine](https://github.com/pkt-gif/custom-vending-machine)**<br><sub>FPGA RTL · TEAM</sub> | **06 · Mission Computer Safety SoC**<br><sub>HW/SW CO-DESIGN · TEAM</sub> |
|:---|:---|
| [![AXI4-Lite vending machine demo](https://img.youtube.com/vi/7eshwTPMTOo/hqdefault.jpg)](https://www.youtube.com/watch?v=7eshwTPMTOo) | <img src="./assets/mission-soc-cover.svg" alt="Mission Computer Safety SoC architecture cover" width="100%"> |
| **FLOW**<br>`Order` → `AXI Master FSM` → `Stock / Dispense` | **FLOW**<br>`Heartbeat / Fault` → `Safety FSM` → `Output Isolation` |
| **MY PART**<br>`AXI Master` · `5-channel Handshake` · `Board UI` | **MY IP**<br>`4-state FSM` · `SAFE_MODE Latch` · `Manual Recovery` |
| `Basys 3` `Verilog` `AXI4-Lite` `Vivado` | `MicroBlaze` `Verilog` `AXI4-Lite` `Vitis` |
| [Repository ↗](https://github.com/pkt-gif/custom-vending-machine) · [Demo ▶](https://www.youtube.com/watch?v=7eshwTPMTOo) | `Safety Controller IP` · `Educational Prototype` |

---

## Toolbox

`C` · `Python` · `STM32 HAL` · `FreeRTOS` · `CAN` · `UART` · `I²C` · `PWM` · `ADC` · `GPIO/EXTI`<br>
`Verilog HDL` · `Vivado` · `Vitis` · `MicroBlaze` · `AXI4-Lite` · `OpenCV` · `YOLO11n` · `NCNN`

## Education & Qualifications

- **대한상공회의소 경기인력개발원** — 온디바이스 AI 반도체 설계 과정 · 2026.02–2026.09 수료 예정
- **가천대학교 전자공학과** · 2018.02–2020.08
- **TOEIC Speaking IH** · **1종 보통 운전면허**

---

<div align="center">

**동작 근거를 코드와 검증 결과로 설명하는 엔지니어가 되겠습니다.**

</div>
