🌡️ STM32 Smart Fan Controller (AHT20 + OLED + Relay)

An IoT-style embedded system built on the **KEYSKING STM32 Tutorial Board**, integrating a **temperature & humidity sensor (AHT20)**, an **OLED display**, and a **relay-controlled cooling fan**.  
The system automatically turns the fan on when temperature exceeds the set threshold and displays real-time environmental data.

---

## 🧠 Features
✅ Real-time **temperature & humidity monitoring** via AHT20  
✅ **OLED screen** (I2C) displays temperature and humidity  
✅ **Relay-controlled fan** turns on automatically when hot  
✅ **RGB indicator** changes color based on system state  
✅ **Modular C structure** for easy expansion (AHT20, OLED, Relay modules)  
✅ Fully compatible with **STM32CubeIDE**

---

## 🧰 Hardware Overview

| Component | Description | STM32 Pins | Notes |
|------------|--------------|-------------|-------|
| **AHT20** | Temperature & Humidity Sensor | PB6 (SCL), PB7 (SDA) | I2C1 |
| **OLED Display** | 0.96" 128×64 I2C Screen | PB8 (SCL), PB9 (SDA) | I2C2 |
| **Relay Module** | Controls Fan Power | PA0 | Active High |
| **RGB LED** | Status Indication | PA1–PA3 | Optional |
| **Encoder / Keys** | Manual control | PA4–PA6 | Optional |

💡 You can replace the relay output with a MOSFET or PWM-controlled driver to achieve variable fan speed.

---

## 🖥️ System Workflow

```text
AHT20 Sensor --> STM32 I2C --> OLED Display
                    │
                    └──> Compare Temperature
                          │
                          ├─> > 28°C → Turn ON Relay → Fan ON
                          └─> ≤ 28°C → Turn OFF Relay → Fan OFF
Software Architecture
Core/
│
├── Inc/
│   ├── aht20.h        # AHT20 sensor header
│   ├── oled.h         # OLED driver header
│   ├── relay.h        # Relay control header
│   └── main.h
│
├── Src/
│   ├── aht20.c        # I2C sensor implementation
│   ├── oled.c         # Display driver
│   ├── relay.c        # Fan relay logic
│   └── main.c         # Main control loop
│
├── README.md
└── LICENSE
