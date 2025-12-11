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
    A[RFID authentication using MFRC522]
    B[OLED UI using SSD1306]
    C[Potentiometer candidate selection]
    D[Push button confirmation]
    E[Buzzer feedback]
    F[Anti double voting logic]
    G[Show total vote count]
    H[LED activity indicator]

    A --> B --> C --> D --> E --> F --> G --> H


flowchart LR
    ROOT[RFID-Voting-System]
    C[Core]
    D[Drivers]
    DOC[Docs]
    A[Assets]
    P[ProjectFiles]

    ROOT --> C
    ROOT --> D
    ROOT --> DOC
    ROOT --> A
    ROOT --> P

    C --> C1[main.c]
    C --> C2[voting.c]
    C --> C3[mfrc522.c]

    D --> D1[spi.c]
    D --> D2[ssd1306_i2c.c]
    D --> D3[adc_button.c]

    DOC --> DOC1[README.md]
    DOC --> DOC2[WIRING.md]

    A --> A1[preview.png]

    P --> IOC[RFID_Voting_System.ioc]


pie
    title Hardware Components
    "MCU STM32F401" : 25
    "RFID MFRC522" : 25
    "OLED SSD1306" : 20
    "Peripherals" : 30


flowchart TB

    subgraph MFRC522 SPI Pins
        PA4[SDA / CS -> PA4]
        PA5[SCK -> PA5]
        PA7[MOSI -> PA7]
        PA6[MISO -> PA6]
        PB0[RST -> PB0]
        IRQ[IRQ -> Not used]
    end

    subgraph SSD1306 I2C Pins
        PB6[SCL -> PB6]
        PB7[SDA -> PB7]
    end

    subgraph Other Peripherals
        BTN[Button -> PA0]
        POT[Potentiometer -> PA1]
        BUZ[Buzzer -> PB2]
        LED[LED -> PC13]
    end

    MCU[STM32F401] --> PA4 & PA5 & PA7 & PA6 & PB0
    MCU --> PB6 & PB7
    MCU --> BTN & POT & BUZ & LED







