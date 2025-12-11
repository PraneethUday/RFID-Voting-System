# 🚀 RFID Voting System — STM32F401 + MFRC522 + SSD1306

A fully working **RFID based electronic voting system** developed using **STM32CubeIDE**, **MFRC522 RFID Reader (SPI)**, **SSD1306 OLED Display (I2C register level)**, **Potentiometer (ADC)** for selecting candidates, and **Push Button + Buzzer** for UI controls.

This project demonstrates an embedded, real time, secure voting flow where each authorized RFID card can vote only once.

---

<p align="center">
  <img alt="project" src="https://img.shields.io/badge/PROJECT-RFID%20Voting-blue?style=flat-square" />
  <img alt="mcu" src="https://img.shields.io/badge/MCU-STM32F401-success?style=flat-square" />
  <img alt="rfid" src="https://img.shields.io/badge/RFID-MFRC522-orange?style=flat-square" />
  <img alt="oled" src="https://img.shields.io/badge/OLED-SSD1306-lightgrey?style=flat-square" />
  <img alt="ide" src="https://img.shields.io/badge/IDE-STM32CubeIDE-informational?style=flat-square" />
</p>

---

## 📌 Features (Mermaid flowchart)

```mermaid
flowchart TB
  F1[RFID authentication using MFRC522] --> F2[OLED UI using SSD1306]
  F2 --> F3[Potentiometer for candidate selection]
  F3 --> F4[Push button for vote confirmation]
  F4 --> F5[Buzzer feedback for valid or invalid card]
  F5 --> F6[Anti double voting logic]
  F6 --> F7[Show total vote count on long button press]
  F7 --> F8[LED activity indicator for RFID scans]

  style F1 fill:#0ea5e9,stroke:#0a3e61,color:#fff
  style F2 fill:#10b981,stroke:#094c36,color:#fff
  style F3 fill:#f59e0b,stroke:#7a4f00,color:#fff
  style F4 fill:#8b5cf6,stroke:#3a2359,color:#fff
  style F5 fill:#ef4444,stroke:#5f1515,color:#fff
  style F6 fill:#06b6d4,stroke:#074b52,color:#fff
  style F7 fill:#60a5fa,stroke:#123a66,color:#fff
  style F8 fill:#94a3b8,stroke:#2b3a45,color:#fff

flowchart LR
  R["RFID-Voting-System"]
  C["Core"]
  D["Drivers"]
  DOC["Docs"]
  A["Assets"]
  P["ProjectFiles"]
  R --> C
  R --> D
  R --> DOC
  R --> A
  R --> P

  C --> C1["main.c"]
  C --> C2["voting.c"]
  C --> C3["mfrc522.c"]

  D --> D1["spi.c"]
  D --> D2["i2c_ssd1306.c"]
  D --> D3["adc_button.c"]

  DOC --> DOC1["README.md"]
  DOC --> DOC2["WIRING.md"]

  A --> IMG1["readme-preview.png"]

  P --> IOC["RFID_Voting_System.ioc"]

pie
  "MCU STM32F401": 25
  "RFID MFRC522": 25
  "OLED SSD1306": 20
  "Peripherals Pot Button Buzzer LED": 30

flowchart TB
  subgraph MFRC522_SPI["MFRC522 SPI connections"]
    M1["SDA CS  -> PA4"]
    M2["SCK      -> PA5"]
    M3["MOSI     -> PA7"]
    M4["MISO     -> PA6"]
    M5["RST      -> PB0"]
    M6["IRQ      -> not used"]
  end

  subgraph SSD1306_I2C["SSD1306 I2C connections"]
    S1["SCL -> PB6"]
    S2["SDA -> PB7"]
  end

  subgraph OTHER["Other peripherals"]
    O1["Button active low -> PA0"]
    O2["Potentiometer ADC -> PA1"]
    O3["Buzzer -> PB2"]
    O4["LED active low -> PC13"]
  end

  MFRC522_SPI --> MCU["MCU STM32F401"]
  SSD1306_I2C --> MCU
  OTHER --> MCU

flowchart LR
  B1["RFID Auth 85%"] --> B2
  B2["OLED UI 65%"] --> B3
  B3["Pot and Button 95%"] --> End
  style B1 fill:#e6faff,stroke:#cfeefd
  style B2 fill:#ecfff2,stroke:#dff6e8
  style B3 fill:#fff8e6,stroke:#fdeacf

pie
  "MCU STM32F401": 25
  "RFID MFRC522": 25
  "OLED SSD1306": 20
  "Peripherals": 30




