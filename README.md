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

| MCU CONTROL | REAL-TIME | INTERFACE | EXTENSION |
|:---:|:---:|:---:|:---:|
| `C` `STM32F4`<br>`HAL` `FSM` | `FreeRTOS`<br>`Task` `Mutex` | `CAN` `UART`<br>`I²C` `PWM` | `FPGA SoC`<br>`Edge AI` |

> 상태와 메시지의 경계를 먼저 정의하고, 센서–판단–구동의 흐름을 실제 하드웨어에서 검증합니다.

---

## Featured Firmware

| 01 · [Object-Detecting Autonomous Taxi](https://github.com/pkt-gif/object-detecting-autonomous-taxi) | 02 · [FreeRTOS Autonomous Robotaxi](https://github.com/pkt-gif/robotaxi) |
|:---|:---|
| [![Object-detecting autonomous taxi demo](https://img.youtube.com/vi/wJaPBZJurDA/hqdefault.jpg)](https://www.youtube.com/watch?v=wJaPBZJurDA) | [![FreeRTOS autonomous robotaxi demo](https://img.youtube.com/vi/1cFvFcStp3M/hqdefault.jpg)](https://www.youtube.com/shorts/1cFvFcStp3M) |
| `STM32F446RE` `FreeRTOS` `CAN`<br>`Raspberry Pi 4` `YOLO11n/NCNN` | `STM32F411RE` `FreeRTOS`<br>`UART` `PWM` `HC-SR04` |
| **CORE**<br>객체 탐지 결과와 초음파 데이터를 결합해 `STOP / SLOW / GO` 주행 상태 제어 | **CORE**<br>센서 측정·자율주행 판단·수동 제어를 3개 Task로 분리 |
| **IMPLEMENTED**<br>CAN 메시지·주행 FSM, 320×320 NCNN 모델, 차동 구동 로직 | **IMPLEMENTED**<br>`SensorTask / DriveTask / ManualTask`, Mutex 데이터 공유, P 제어 조향 |
| **MY PART**<br>시스템 아키텍처, 교통 객체 6종 데이터셋, 센서 융합 | **SOLO PROJECT**<br>`manual_mode`로 자율주행과 Bluetooth 수동 명령의 실행 경로 분리 |
| [Repository ↗](https://github.com/pkt-gif/object-detecting-autonomous-taxi) · [Demo ▶](https://www.youtube.com/watch?v=wJaPBZJurDA) | [Repository ↗](https://github.com/pkt-gif/robotaxi) · [Demo ▶](https://www.youtube.com/shorts/1cFvFcStp3M) · [Autonomous ▶](https://www.youtube.com/shorts/8N2YOQ3bM_4) |

---

## Systems Portfolio

| No. | PROJECT | WHAT I BUILT | STACK |
|:---:|:---|:---|:---|
| **03** | [STM32 Lift Controller](https://github.com/pkt-gif/stm32-elevator) | 키패드 인증, 스텝모터 승강, 포토인터럽터 상·하한 제한, UART 점검 명령 | `STM32` `UART` `Stepper` |
| **04** | Mission Computer Fault-Response SoC | Heartbeat/Fault 입력에 따라 출력을 격리하는 Safety Controller IP의 4-state FSM, `SAFE_MODE` Latch, Manual Recovery | `MicroBlaze` `Verilog` `AXI4-Lite` |
| **05** | [AXI4-Lite Vending Machine](https://github.com/pkt-gif/custom-vending-machine) | Master Interface의 5채널 Handshake, 버튼·스위치 UI, Basys 3 통합 | `Verilog` `FSM` `Vivado` |
| **06** | [Smart Fish Tank](https://github.com/pkt-gif/Smart-fish-tank) | ADC 차분을 이용한 상대 탁도 상태 판정과 LCD·RGB LED 표시 | `ATmega128A` `ADC` `I²C` |

<p align="center">
  <a href="https://www.youtube.com/watch?v=AVxfVoIqJPs">Lift Demo ▶</a> ·
  <a href="https://www.youtube.com/watch?v=7eshwTPMTOo">Vending Demo ▶</a> ·
  <a href="https://www.youtube.com/watch?v=u2zzdcHJl2s">Fish Tank Demo ▶</a>
</p>

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
