# 🚀 RFID Voting System — STM32F401 + MFRC522 + SSD1306

A fully working **RFID-based electronic voting system** developed using **STM32CubeIDE**, **MFRC522 RFID Reader (SPI)**, **SSD1306 OLED Display (I2C – register level)**, **Potentiometer (ADC)** for selecting candidates, and **Push Button + Buzzer** for UI controls.

This project demonstrates an embedded, real-time, secure voting flow where each authorized RFID card can vote only once.

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
  A[RFID-based voter authentication<br/>(MFRC522)] --> B[OLED UI<br/>(SSD1306, I2C register-level)]
  B --> C[Potentiometer for candidate selection<br/>(ADC on PA1)]
  C --> D[Push-button for vote confirmation<br/>(active-low PA0)]
  D --> E[Buzzer feedback for valid/invalid card<br/>(PB2)]
  E --> F[Anti-double-voting logic<br/>(each authorized UID votes once)]
  F --> G[Show total vote count on long button press]
  G --> H[LED activity indicator<br/>(PC13)]
  style A fill:#0ea5e9,stroke:#0a3e61,color:#fff
  style B fill:#10b981,stroke:#094c36,color:#fff
  style C fill:#f59e0b,stroke:#7a4f00,color:#fff
  style D fill:#8b5cf6,stroke:#3a2359,color:#fff
  style E fill:#ef4444,stroke:#5f1515,color:#fff
  style F fill:#06b6d4,stroke:#074b52,color:#fff
  style G fill:#60a5fa,stroke:#123a66,color:#fff
  style H fill:#94a3b8,stroke:#2b3a45,color:#fff

flowchart LR
  root["RFID-Voting-System/"]
  core["/Core/"]
  drivers["/Drivers/"]
  docs["/Docs/"]
  assets["/Assets/"]
  ideproj["/STM32CubeIDE_Project/"]
  root --> core
  root --> drivers
  root --> docs
  root --> assets
  root --> ideproj

  core --> mainc["main.c"]
  core --> votingc["voting.c"]
  core --> mfrc522c["mfrc522.c"]
  drivers --> spi["spi.c / spi.h"]
  drivers --> ssd["i2c_ssd1306.c / ssd1306.h"]
  drivers --> adcbtn["adc_button.c / adc_button.h"]
  docs --> readme["README.md"]
  docs --> wiring["WIRING.md"]
  assets --> image["readme-preview.png"]
  ideproj --> ioc["RFID_Voting_System.ioc"]

pie
  title Hardware Composition (example split)
  "MCU (STM32F401)": 25
  "RFID (MFRC522)": 25
  "OLED (SSD1306)": 20
  "Peripherals (Pot/Button/Buzzer/LED)": 30

flowchart TB
  subgraph MFRC522_SPI ["MFRC522 (SPI1)"]
    SDA["SDA / CS → PA4"]
    SCK["SCK → PA5"]
    MOSI["MOSI → PA7"]
    MISO["MISO → PA6"]
    RST["RST → PB0"]
    IRQ["IRQ → (not used)"]
  end

  subgraph SSD1306_I2C ["SSD1306 (I2C)"]
    SCL["SCL → PB6"]
    SDA2["SDA → PB7"]
  end

  subgraph OTHER ["Other Peripherals"]
    BTN["Button (active-low) → PA0"]
    POT["Potentiometer (ADC1_IN1) → PA1"]
    BUZ["Buzzer → PB2"]
    LED["LED (Active-low) → PC13"]
  end

  MFRC522_SPI --> MCU["STM32F401"]
  SSD1306_I2C --> MCU
  OTHER --> MCU

flowchart LR
  A[RFID Auth — ██████████████████████████ 85%] --> B
  B[OLED UI — █████████████████████ 65%] --> C
  C[Pot/Button — █████████████████████████████ 95%] --> D
  style A fill:#e6faff,stroke:#cfeefd
  style B fill:#ecfff2,stroke:#dff6e8
  style C fill:#fff8e6,stroke:#fdeacf

pie
  "MCU (STM32F401)": 25
  "RFID (MFRC522)": 25
  "OLED (SSD1306)": 20
  "Peripherals": 30
