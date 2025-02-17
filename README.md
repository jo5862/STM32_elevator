<br><br>
## STM32 마이크로컨트롤러를 이용한 **엘리베이터 제어 시스템**<br>
스탭 모터를 통한 층 이동<br>
서보 모터를 이용한 문 열기/닫기 및 LCD 화면으로 현재 상태 표시<br>
포토인터럽터 발생시 정지<br>
타이머를 이용한 논블락킹 구현<br>

<br><br>

# 🛗 Elevator Control System

이 프로젝트는 STM32 마이크로컨트롤러를 사용하여 엘리베이터 시스템을 제어하는 프로그램입니다. 스탭 모터를 이용한 엘리베이터의 층 이동과 서보 모터를 이용한 문 열기/닫기 기능을 구현하며, LCD 화면에 현재 상태와 메시지를 표시합니다.

## ✨ 주요 기능
- **층 이동**: 버튼을 눌러 원하는 층으로 이동합니다. 각 층에 도달하면 LCD 화면에 도착 메시지가 표시됩니다.
- **모터 제어**: 스탭 모터를 이용해 엘리베이터를 원하는 층으로 이동시킵니다.
- **서보 모터 제어**: 엘리베이터 문을 열고 닫는 서보 모터를 제어합니다.
- **LCD 출력**: 현재 층, 도착 메시지, 엘리베이터의 상태를 LCD 화면에 출력합니다.
- **포토 인터럽트**: 각 층에 도달했을 때 인터럽트를 이용하여 모터를 정지시키고 메시지를 출력합니다.

---

## 🛠 코드의 주요 흐름

1. **사용자가 버튼을 눌러 원하는 층을 선택**합니다.
2. **층 이동 및 모터 제어**
   - **스탭 모터**를 이용해 엘리베이터가 선택한 층으로 이동합니다.
   - 각 층에 도달하면 **LCD 화면에 도착 메시지**를 표시하고, **서보 모터**로 문을 열고 닫습니다.
3. **포토 인터럽트 콜백**:
   - 각 층에 도달하면 **포토 인터럽트를 통해 모터를 정지**하고 도착 메시지를 출력합니다.
4. **타이머 콜백**:
   - 모터가 일정 시간마다 회전하도록 하는 타이머 콜백 함수가 포함되어 있습니다.

---

## 🖥 실행 방법

### 1️⃣ 필수 소프트웨어
- STM32CubeIDE 또는 Keil을 설치합니다.

### 2️⃣ 프로젝트 열기
1. STM32CubeIDE 또는 Keil을 통해 프로젝트를 엽니다.
2. STM32CubeMX를 통해 설정을 조정하고, 마이크로컨트롤러에 맞게 빌드합니다.

### 3️⃣ 실행
- 빌드 후 **STM32 마이크로컨트롤러에 코드를 다운로드**하여 실행합니다.

---

## 📂 프로젝트 구조

📂 Core
│── 📂 Src  
│   ├── I2C_LCD.c                        # LCD 통신 관련 코드  
│   ├── gpio.c                           # GPIO 설정 코드  
│   ├── i2c.c                            # I2C 통신 관련 코드  
│   ├── main.c                           # 메인 코드 (엘리베이터 제어 및 LCD 출력)  
│   ├── stepper.c                        # 스탭 모터 제어 코드  
│   ├── stm32f4xx_hal_msp.c              # HAL MSP 초기화 코드  
│   ├── stm32f4xx_it.c                   # 인터럽트 핸들러 코드  
│   ├── syscalls.c                       # 시스템 콜 관련 코드  
│   ├── sysmem.c                         # 시스템 메모리 관련 코드  
│   ├── system_stm32f4xx.c               # 시스템 초기화 코드  
│   ├── tim.c                            # 타이머 설정 코드  
│   └── usart.c                          # USART 설정 코드  
│  
│── 📂 Inc  
│   ├── I2C_LCD.h                        # LCD 통신 관련 헤더 파일  
│   ├── gpio.h                           # GPIO 설정 관련 헤더 파일  
│   ├── i2c.h                            # I2C 통신 관련 헤더 파일  
│   ├── main.h                           # 메인 코드 관련 헤더 파일  
│   ├── stepper.h                        # 스탭 모터 관련 헤더 파일  
│   ├── stm32f4xx_hal_conf.h             # STM32F4 HAL 설정 파일  
│   ├── stm32f4xx_it.h                   # 인터럽트 핸들러 관련 헤더 파일  
│   ├── tim.h                            # 타이머 설정 헤더 파일  
│   └── usart.h                          # USART 설정 헤더 파일  
│  
│── README.md                            # 프로젝트 설명 파일  
└──


---

## 💻 빌드 및 설치

이 프로젝트는 STM32CubeIDE 또는 Keil을 사용하여 빌드할 수 있습니다. 필요한 설정 파일들은 STM32CubeMX를 통해 생성됩니다.

1. STM32CubeIDE 또는 Keil을 통해 프로젝트를 엽니다.
2. 프로젝트 설정에 맞게 빌드를 진행합니다.
3. 마이크로컨트롤러에 코드를 다운로드하여 실행합니다.

---

## 📜 라이선스

이 프로젝트는 [MIT 라이선스](LICENSE) 하에 배포됩니다.
