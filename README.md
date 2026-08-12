<p align="center">
  <img src="./assets/profile-banner.svg" alt="Park Kitae — Embedded Firmware Engineer" width="100%">
</p>

<div align="center">

### MCU 위에서 센싱·판단·통신·구동이 하나의 시스템으로 동작하도록 만듭니다.

STM32·FreeRTOS를 중심으로 Task/FSM과 통신·제어 로직을 설계하고,<br>
**실제 하드웨어에서 동작을 검증하는 임베디드 펌웨어 엔지니어 박기태입니다.**

<a href="mailto:pkikit95@gmail.com"><img src="https://img.shields.io/badge/Email-pkikit95%40gmail.com-0F766E?style=flat-square&logo=gmail&logoColor=white" alt="Email"></a>
<a href="https://github.com/pkt-gif"><img src="https://img.shields.io/badge/GitHub-pkt--gif-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub"></a>

</div>

---

## Engineering Focus

| MCU FIRMWARE | RTOS & INTERFACES | SYSTEM EXTENSION |
|:---:|:---:|:---:|
| `C` `STM32F4`<br>`HAL` `FSM` | `FreeRTOS` `Task/Mutex`<br>`CAN` `UART` `I²C` `PWM` | `Edge AI`<br>`FPGA SoC` |

> 상태와 메시지의 경계를 먼저 정의하고, 센서–판단–구동의 흐름을 실제 하드웨어에서 검증합니다.

---

## Engineering Projects

영상 이미지를 누르면 각 프로젝트의 실제 동작을 확인할 수 있습니다.

### 01 · [Object-Detecting Autonomous Taxi](https://github.com/pkt-gif/object-detecting-autonomous-taxi)

`TEAM` · `FIRMWARE + EDGE AI`

<p align="center">
  <a href="https://www.youtube.com/watch?v=wJaPBZJurDA"><img src="https://img.youtube.com/vi/wJaPBZJurDA/hqdefault.jpg" alt="Object-detecting autonomous taxi demo" width="480"></a>
</p>

<table>
  <tr>
    <td width="21%"><strong>PROJECT</strong></td>
    <td>Raspberry Pi 4에서 USB 웹캠 영상을 YOLO11n/NCNN으로 처리해 6종 교통 객체를 인식하고 <code>STOP / SLOW / GO</code> 상태를 CAN으로 전달합니다. STM32F446RE는 이 상태와 3방향 초음파 값을 결합해 차동 구동을 제어하고, 포토인터럽터 기반 이동 거리와 요금을 LCD에 표시합니다.</td>
  </tr>
  <tr>
    <td><strong>SYSTEM FLOW</strong></td>
    <td><code>Camera</code> → <code>YOLO11n/NCNN</code> → <code>CAN</code> → <code>STM32 Drive FSM + Ultrasonic</code> → <code>Differential Drive</code></td>
  </tr>
  <tr>
    <td><strong>TECH STACK</strong></td>
    <td><code>STM32F446RE</code> <code>C/HAL</code> <code>FreeRTOS</code> <code>CAN</code> <code>Raspberry Pi 4</code> <code>Python/OpenCV</code> <code>YOLO11n/NCNN</code> <code>I²C/PWM/EXTI</code></td>
  </tr>
  <tr>
    <td><strong>MY ROLE</strong></td>
    <td>전체 시스템 아키텍처 설계 · 교통 객체 6종 데이터셋 구축 · 3방향 초음파 센서 융합 · 차동 구동 기반 주행·조향 로직</td>
  </tr>
  <tr>
    <td><strong>TROUBLESHOOTING</strong></td>
    <td><strong>문제</strong> — 인접 초음파 센서의 반사파가 섞이면서 거리값이 불안정해질 수 있었습니다.<br><strong>원인</strong> — 이전 채널의 Echo가 사라지기 전에 다음 센서를 Trigger하면 Cross-talk가 발생할 수 있었습니다.<br><strong>해결</strong> — 좌·전방·우 센서를 40 ms 간격으로 순차 측정하고, 세 측정값을 Mutex 안에서 한 번에 갱신해 DriveTask가 서로 다른 측정 주기의 값을 섞어 읽지 않도록 했습니다.</td>
  </tr>
</table>

<p align="center"><a href="https://github.com/pkt-gif/object-detecting-autonomous-taxi">Repository ↗</a> · <a href="https://www.youtube.com/watch?v=wJaPBZJurDA">Demo ▶</a></p>

---

### 02 · [FreeRTOS Autonomous Robotaxi](https://github.com/pkt-gif/robotaxi)

`SOLO` · `RTOS FIRMWARE`

<p align="center">
  <a href="https://www.youtube.com/shorts/1cFvFcStp3M"><img src="https://img.youtube.com/vi/1cFvFcStp3M/hqdefault.jpg" alt="FreeRTOS autonomous robotaxi demo" width="480"></a>
</p>

<table>
  <tr>
    <td width="21%"><strong>PROJECT</strong></td>
    <td>STM32F411RE에서 센서 수집, 자율주행 판단, Bluetooth 수동 제어를 3개의 FreeRTOS Task로 분리한 개인 프로젝트입니다. 3방향 초음파 거리로 긴급 회피·코너링·일반 주행을 분기하고, 일반 주행에서는 좌우 거리 오차를 이용한 P 제어로 모터 속도를 보정합니다.</td>
  </tr>
  <tr>
    <td><strong>SYSTEM FLOW</strong></td>
    <td><code>3-Way Ultrasonic</code> → <code>SensorTask + Mutex</code> → <code>DriveTask / ManualTask</code> → <code>Motor · LED · Buzzer</code></td>
  </tr>
  <tr>
    <td><strong>TECH STACK</strong></td>
    <td><code>STM32F411RE</code> <code>C/HAL</code> <code>FreeRTOS</code> <code>UART Interrupt</code> <code>Bluetooth</code> <code>PWM</code> <code>HC-SR04 ×3</code> <code>IR Sensor</code></td>
  </tr>
  <tr>
    <td><strong>MY ROLE</strong></td>
    <td>3-Task 구조와 우선순위 · Mutex 기반 센서 데이터 공유 · 초음파 장애물 회피와 P 제어 조향 · Bluetooth 자율/수동 모드 전환 · 모터·LED·부저 제어</td>
  </tr>
  <tr>
    <td><strong>TROUBLESHOOTING</strong></td>
    <td><strong>문제</strong> — 초음파 센서가 순간적으로 응답하지 않으면 0 cm가 주행 판단에 잘못된 긴급 회피 입력으로 전달될 수 있었습니다.<br><strong>원인</strong> — Echo 상승이 시작되지 않거나 High Pulse가 비정상적으로 유지되는 센서 미응답 경로가 있었습니다.<br><strong>해결</strong> — 5 ms/30 ms Timeout으로 무한 대기를 차단하고, 0 대신 채널별 마지막 정상값을 유지했습니다. 좌우 값은 조향에 필요한 60 cm 범위로 제한해 제어 입력을 안정화했습니다.</td>
  </tr>
</table>

<p align="center"><a href="https://github.com/pkt-gif/robotaxi">Repository ↗</a> · <a href="https://www.youtube.com/shorts/1cFvFcStp3M">Manual Demo ▶</a> · <a href="https://www.youtube.com/shorts/8N2YOQ3bM_4">Autonomous Demo ▶</a></p>

---

### 03 · [Mission Computer Fault-Response SoC](https://github.com/pkt-gif/mission-computer-fault-response-soc)

`TEAM` · `HW/SW CO-DESIGN` · `EDUCATIONAL PROTOTYPE`

<p align="center">
  <a href="https://www.youtube.com/watch?v=G8UkcHLjhrM"><img src="https://img.youtube.com/vi/G8UkcHLjhrM/hqdefault.jpg" alt="Mission Computer fault-response SoC demo" width="480"></a>
</p>

<table>
  <tr>
    <td width="21%"><strong>PROJECT</strong></td>
    <td>3개 하위 장치의 Heartbeat와 오류를 FPGA Custom IP가 병렬 감시하고, 심각도와 지속시간에 따라 시스템을 <code>NORMAL / WARNING / DEGRADED / SAFE_MODE</code>로 전환하는 MicroBlaze 기반 교육용 SoC입니다. 일반 고장에서는 해당 장치 출력만 격리하고 Critical·다중 고장에서는 전체 출력을 차단하며, MicroBlaze와 PC GUI는 설정·관찰·기록을 담당합니다.</td>
  </tr>
  <tr>
    <td><strong>SYSTEM FLOW</strong></td>
    <td><code>3 Devices</code> → <code>Heartbeat Monitor / Fault Manager</code> → <code>Safety Controller</code> → <code>Output Gate + IRQ</code> → <code>MicroBlaze / UART GUI</code></td>
  </tr>
  <tr>
    <td><strong>TECH STACK</strong></td>
    <td><code>Basys 3</code> <code>MicroBlaze V</code> <code>Verilog HDL</code> <code>Vivado</code> <code>AXI4-Lite</code> <code>AXI INTC/UARTLite/GPIO</code> <code>Vitis C</code> <code>Python/PySide6</code></td>
  </tr>
  <tr>
    <td><strong>MY ROLE</strong></td>
    <td>Safety Controller Core·AXI Wrapper · 4-state FSM · 장치별 출력 격리 · <code>SAFE_MODE</code> Latch · Manual Recovery · 상태 변화 IRQ · Core/AXI Testbench 설계. 세 Custom IP와 MicroBlaze·GUI의 보드 통합은 3인이 공동 수행했습니다.</td>
  </tr>
  <tr>
    <td><strong>TROUBLESHOOTING</strong></td>
    <td><strong>문제</strong> — 9600 bps UART 송신이 길어질 때 GUI 명령이 유실되거나 Heartbeat Timeout이 잘못 발생했습니다.<br><strong>원인</strong> — Blocking UART 송신이 RX 처리와 주기적인 Heartbeat 생성을 막았습니다.<br><strong>해결</strong> — 공동 통합 과정에서 RX Ring Buffer와 자체 <code>PROTO_Printf</code>를 도입하고, 송신 전에 <code>HBGEN_Pump</code>를 호출하도록 수정해 통신 중에도 Heartbeat와 명령 수신이 유지되도록 했습니다.</td>
  </tr>
</table>

<p align="center"><a href="https://github.com/pkt-gif/mission-computer-fault-response-soc">Repository ↗</a> · <a href="https://www.youtube.com/watch?v=G8UkcHLjhrM">Demo ▶</a></p>

---

### 04 · [AXI4-Lite Custom Vending Machine](https://github.com/pkt-gif/custom-vending-machine)

`TEAM` · `FPGA RTL`

<p align="center">
  <a href="https://www.youtube.com/watch?v=7eshwTPMTOo"><img src="https://img.youtube.com/vi/7eshwTPMTOo/hqdefault.jpg" alt="AXI4-Lite custom vending machine demo" width="480"></a>
</p>

<table>
  <tr>
    <td width="21%"><strong>PROJECT</strong></td>
    <td>5종 음료와 당도·얼음양을 각각 5단계로 선택하고, 결제·재고·잔돈·배출까지 처리하는 Basys 3 기반 RTL 자판기입니다. 메인 FSM과 재고 코어 사이의 데이터를 AXI4-Lite Master/Slave로 교환하고, LED·서보모터의 완료 신호를 확인한 뒤 다음 상태로 진행합니다.</td>
  </tr>
  <tr>
    <td><strong>SYSTEM FLOW</strong></td>
    <td><code>Button / Switch / Coin</code> → <code>Main FSM + AXI4-Lite</code> → <code>Payment / Inventory</code> → <code>Servo · LED Bar · 7-Segment</code></td>
  </tr>
  <tr>
    <td><strong>TECH STACK</strong></td>
    <td><code>Basys 3 / Artix-7</code> <code>Verilog HDL</code> <code>Vivado</code> <code>AXI4-Lite</code> <code>FSM</code> <code>PWM</code> <code>7-Segment</code> <code>LED Bar</code> <code>Servo Motor</code></td>
  </tr>
  <tr>
    <td><strong>MY ROLE</strong></td>
    <td>AXI4-Lite Master Interface · <code>AW / W / B / AR / R</code> 5개 채널 Handshake · 3회 Write/3회 Read Transaction Sequence · 버튼·스위치 UI · Basys 3 하드웨어 통합</td>
  </tr>
  <tr>
    <td><strong>TROUBLESHOOTING</strong></td>
    <td><strong>문제</strong> — LED와 서보모터의 완료 신호가 짧은 Pulse여서 Main FSM이 완료 시점을 놓칠 수 있었습니다.<br><strong>원인</strong> — 완료 Pulse의 유지 시간과 FSM이 해당 신호를 소비하는 시점이 일치하지 않았습니다.<br><strong>해결</strong> — <code>DONE / SERVO / CHANGE</code> 완료 Pulse를 각각 Latch하고, 대응 상태가 종료될 때까지 유지하도록 통합 로직을 구성했습니다. Testbench에는 스위치 유지와 지연된 반환 입력 시나리오를 반영했습니다.</td>
  </tr>
</table>

<p align="center"><a href="https://github.com/pkt-gif/custom-vending-machine">Repository ↗</a> · <a href="https://www.youtube.com/watch?v=7eshwTPMTOo">Demo ▶</a></p>

---

### 05 · [STM32 Lift Controller](https://github.com/pkt-gif/stm32-elevator)

`TEAM` · `MCU CONTROL`

<p align="center">
  <a href="https://www.youtube.com/watch?v=AVxfVoIqJPs"><img src="https://img.youtube.com/vi/AVxfVoIqJPs/hqdefault.jpg" alt="STM32 lift controller demo" width="480"></a>
</p>

<table>
  <tr>
    <td width="21%"><strong>PROJECT</strong></td>
    <td>STM32F411RE에서 키패드 인증, 승강·도어 스텝모터, 포토인터럽터 상·하한 감지와 상태 출력을 통합한 리프트 제어 프로토타입입니다. 정상 운전에서는 승강 입력과 물리적 한계를 함께 확인하고, I²C LCD·LED·부저로 상태를 표시하며 비상 시 UART 관리자 점검·복구 흐름으로 전환합니다.</td>
  </tr>
  <tr>
    <td><strong>SYSTEM FLOW</strong></td>
    <td><code>Keypad / Button</code> → <code>Authentication + State Control</code> → <code>Photo Interlock</code> → <code>Lift / Door · LCD · Alarm</code></td>
  </tr>
  <tr>
    <td><strong>TECH STACK</strong></td>
    <td><code>STM32F411RE</code> <code>C/HAL</code> <code>HAL_GetTick</code> <code>GPIO</code> <code>UART RX Interrupt</code> <code>I²C LCD</code> <code>4×4 Keypad</code> <code>Half-step Stepper</code> <code>Photo Interrupter</code></td>
  </tr>
  <tr>
    <td><strong>MY ROLE</strong></td>
    <td>리프트 승강 제어 로직 · 포토인터럽터 기반 상·하한 범위 제한 · 이동 상태에 따른 LED·부저 피드백</td>
  </tr>
  <tr>
    <td><strong>TROUBLESHOOTING</strong></td>
    <td><strong>문제</strong> — 상·하한에 도달한 뒤에도 방향 입력이 유지되면 승강 모터가 기구 범위를 넘어 구동될 위험이 있었습니다.<br><strong>원인</strong> — 버튼 명령만으로는 현재의 물리적 끝 위치를 판단할 수 없었습니다.<br><strong>해결</strong> — 방향을 결정하기 전에 상단·하단 포토인터럽터를 Interlock 조건으로 확인하고, 유효한 방향이 없으면 코일 출력을 차단했습니다. 정상 운전에서는 모터 스텝과 LED·부저 갱신을 <code>HAL_GetTick()</code> 기준으로 분리했습니다.</td>
  </tr>
</table>

<p align="center"><a href="https://github.com/pkt-gif/stm32-elevator">Repository ↗</a> · <a href="https://www.youtube.com/watch?v=AVxfVoIqJPs">Demo ▶</a></p>

---

### 06 · [Smart Fish Tank](https://github.com/pkt-gif/Smart-fish-tank)

`TEAM` · `EMBEDDED SENSING`

<p align="center">
  <a href="https://www.youtube.com/watch?v=u2zzdcHJl2s"><img src="https://img.youtube.com/vi/u2zzdcHJl2s/hqdefault.jpg" alt="Smart fish tank demo" width="480"></a>
</p>

<table>
  <tr>
    <td width="21%"><strong>PROJECT</strong></td>
    <td>ATmega128A 기반으로 상대 탁도 상태 모니터링, 예약 먹이 배급, 레일 청소와 상태 표시를 통합한 스마트 어항 시스템입니다. 조도센서로 얻은 상대적 빛 투과 지표를 3단계로 판정해 I²C LCD·RGB LED로 표시하고, 나쁨 상태에서는 레일 청소 요청으로 연결합니다.</td>
  </tr>
  <tr>
    <td><strong>SYSTEM FLOW</strong></td>
    <td><code>LED OFF/ON ADC</code> → <code>Average + Difference</code> → <code>3-State Decision</code> → <code>LCD / RGB LED / Clean Request</code></td>
  </tr>
  <tr>
    <td><strong>TECH STACK</strong></td>
    <td><code>ATmega128A</code> <code>C</code> <code>ADC</code> <code>I²C LCD</code> <code>GPIO</code> <code>RGB LED</code> <code>DS1302 RTC</code> <code>PWM</code> <code>Servo / DC Motor</code> <code>FSM</code></td>
  </tr>
  <tr>
    <td><strong>MY ROLE</strong></td>
    <td>조도센서 기반 상대 탁도 상태 판정 · LED OFF/ON ADC 평균 측정 · 3단계 임계값 분류 · RGB LED·I²C LCD 상태 표시 연동</td>
  </tr>
  <tr>
    <td><strong>TROUBLESHOOTING</strong></td>
    <td><strong>문제</strong> — 일반 2핀 LED의 광량이 부족해 맑은 물과 탁한 물의 ADC 차이가 명확하게 분리되지 않았습니다.<br><strong>원인</strong> — 측정광이 약하고 조도센서 값에 주변광이 함께 포함돼 절대값만으로 안정적인 판정이 어려웠습니다.<br><strong>해결</strong> — RGB LED 모듈로 광량을 높이고, LED를 끈 주변광 기준값과 켠 측정값을 각각 평균낸 뒤 두 값의 차이를 사용해 상대 탁도를 3단계로 분류했습니다.</td>
  </tr>
</table>

<p align="center"><a href="https://github.com/pkt-gif/Smart-fish-tank">Repository ↗</a> · <a href="https://www.youtube.com/watch?v=u2zzdcHJl2s">Demo ▶</a></p>

---

## Engineering Toolkit

### Core Firmware

<p>
  <img src="https://skillicons.dev/icons?i=c" height="40" alt="C" title="C">
  &nbsp;
  <img src="https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" height="40" alt="STM32" title="STM32">
  &nbsp;
  <img src="https://img.shields.io/badge/FreeRTOS-2B2F77?style=for-the-badge&logo=freertos&logoColor=white" height="40" alt="FreeRTOS" title="FreeRTOS">
</p>

`HAL` · `FSM` · `Task / Mutex` · `CAN` · `UART` · `I²C` · `ADC` · `PWM` · `GPIO / EXTI`

### FPGA & SoC

<p>
  <img src="https://img.shields.io/badge/Verilog-6E4C9A?style=for-the-badge&logoColor=white" height="40" alt="Verilog HDL" title="Verilog HDL">
  &nbsp;
  <img src="https://img.shields.io/badge/Vivado-E01F27?style=for-the-badge&logo=amd&logoColor=white" height="40" alt="Vivado" title="Vivado">
  &nbsp;
  <img src="https://img.shields.io/badge/Vitis-E01F27?style=for-the-badge&logo=amd&logoColor=white" height="40" alt="Vitis" title="Vitis">
  &nbsp;
  <img src="https://img.shields.io/badge/MicroBlaze_V-18212F?style=for-the-badge&logo=amd&logoColor=white" height="40" alt="MicroBlaze V" title="MicroBlaze V">
</p>

`AXI4-Lite` · `Custom IP` · `Interrupt / W1C`

### Edge AI & Vision

<p>
  <img src="https://skillicons.dev/icons?i=python" height="40" alt="Python" title="Python">
  &nbsp;
  <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" height="40" alt="OpenCV" title="OpenCV">
  &nbsp;
  <img src="https://img.shields.io/badge/Raspberry_Pi-A22846?style=for-the-badge&logo=raspberrypi&logoColor=white" height="40" alt="Raspberry Pi" title="Raspberry Pi">
</p>

`YOLO11n` · `NCNN` · `SocketCAN`

### Tools & Verification

<p>
  <img src="https://skillicons.dev/icons?i=git,github" height="40" alt="Git and GitHub" title="Git and GitHub">
</p>

`Self-checking Testbench` · `Waveform Analysis` · `Hardware Integration`

## Education & Qualifications

- **대한상공회의소 경기인력개발원** — 온디바이스 AI 반도체 설계 과정 · 2026.02–2026.09 수료 예정
- **가천대학교 전자공학과** · 2018.02–2020.08
- **TOEIC Speaking IH** · **1종 보통 운전면허**

---

<div align="center">

**동작 근거를 코드와 검증 결과로 설명하는 엔지니어가 되겠습니다.**

</div>
