<!-- README.md — GitHub-friendly, visually rich with SVG + Mermaid (paste whole file) -->

<p align="center">
  <img alt="project" src="https://img.shields.io/badge/PROJECT-RFID%20Voting-blue?style=flat-square" />
  <img alt="mcU" src="https://img.shields.io/badge/MCU-STM32F401-success?style=flat-square" />
  <img alt="rfid" src="https://img.shields.io/badge/RFID-MFRC522-orange?style=flat-square" />
  <img alt="oled" src="https://img.shields.io/badge/OLED-SSD1306-lightgrey?style=flat-square" />
  <img alt="ide" src="https://img.shields.io/badge/IDE-STM32CubeIDE-informational?style=flat-square" />
</p>

# 🚀 RFID Voting System — STM32F401 + MFRC522 + SSD1306

*A fully working **RFID-based electronic voting system** developed using **STM32CubeIDE**, **MFRC522 RFID Reader (SPI)**, **SSD1306 OLED Display (I2C – register level)**, **Potentiometer (ADC)** for selecting candidates, and **Push Button + Buzzer** for UI controls.*

This project demonstrates an embedded, real-time, secure voting flow where each authorized RFID card can vote only once.


---

# 📌 Features
- ✔ **RFID-based voter authentication** using MFRC522  
- ✔ **OLED UI** using SSD1306 (Register-level I2C implementation)  
- ✔ **Potentiometer for candidate selection** (ADC on PA1)  
- ✔ **Push-button for vote confirmation**  
- ✔ **Buzzer feedback** for valid/invalid card  
- ✔ **Anti-double-voting logic** (each authorized UID can vote only once)  
- ✔ **Shows total vote count** on long button press  
- ✔ **LED activity indicator** for RFID scans  
- ✔ Fully working STM32CubeIDE project included in repo

---


### 2) Hardware Composition — Pie Chart (SVG)
<p align="center">
<svg width="380" height="220" viewBox="0 0 380 220" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Hardware composition pie chart">
  <!-- Pie chart center at (140,110), radius 80 -->
  <!-- slices: MCU 25%, RFID 25%, OLED 20%, Peripherals 30% -->
  <g transform="translate(190,110)">
    <!-- Background circle -->
    <circle r="90" fill="#ffffff" stroke="#e6eef8" />
    <!-- Slices drawn as paths -->
    <!-- MCU 25% (0 -> 90deg) -->
    <path d="M 0 0 L 90 0 A 90 90 0 0 1 55.153 64.279 Z" fill="#0ea5e9">
      <animate attributeName="d" dur="0.9s" from="M0 0 L0 0 Z" to="M 0 0 L 90 0 A 90 90 0 0 1 55.153 64.279 Z" fill="freeze" begin="0.0s"/>
    </path>
    <!-- RFID 25% (90deg -> 180deg) -->
    <path d="M 0 0 L 55.153 64.279 A 90 90 0 0 1 -55.153 64.279 Z" fill="#10b981">
      <animate attributeName="d" dur="0.9s" from="M0 0 L0 0 Z" to="M 0 0 L 55.153 64.279 A 90 90 0 0 1 -55.153 64.279 Z" fill="freeze" begin="0.15s"/>
    </path>
    <!-- OLED 20% (180deg -> 252deg) -->
    <path d="M0 0 L -55.153 64.279 A 90 90 0 0 1 -80.903 -2.773 Z" fill="#f59e0b">
      <animate attributeName="d" dur="0.9s" from="M0 0 L0 0 Z" to="M0 0 L -55.153 64.279 A 90 90 0 0 1 -80.903 -2.773 Z" fill="freeze" begin="0.3s"/>
    </path>
    <!-- Peripherals 30% (252deg -> 360deg) -->
    <path d="M0 0 L -80.903 -2.773 A 90 90 0 0 1 90 0 Z" fill="#8b5cf6">
      <animate attributeName="d" dur="0.9s" from="M0 0 L0 0 Z" to="M0 0 L -80.903 -2.773 A 90 90 0 0 1 90 0 Z" fill="freeze" begin="0.45s"/>
    </path>
    <!-- center hole for donut -->
    <circle r="36" fill="#fff" stroke="#fff"/>
  </g>

  <!-- Legend -->
  <g transform="translate(300,40)" font-family="Arial" font-size="11">
    <rect x="0" y="0" width="12" height="12" fill="#0ea5e9"/><text x="18" y="10">MCU (STM32F401) — 25%</text>
    <rect x="0" y="20" width="12" height="12" fill="#10b981"/><text x="18" y="30">RFID (MFRC522) — 25%</text>
    <rect x="0" y="40" width="12" height="12" fill="#f59e0b"/><text x="18" y="50">OLED (SSD1306) — 20%</text>
    <rect x="0" y="60" width="12" height="12" fill="#8b5cf6"/><text x="18" y="70">Peripherals (Buttons/Buzzers/Pot) — 30%</text>
  </g>
</svg>
</p>

> **Text fallback (for accessibility / search):** MCU 25%, RFID 25%, OLED 20%, Peripherals 30%.

---

## 📂 Repository Structure

| Folder / File | Description |
|---------------|-------------|
| **Core/** | Main application source code |
| ├── **Inc/** | Header files (*.h) |
| ├── **Src/** | Source files (*.c) |
| └── **Startup/** | Startup files & vector table |
| **Debug/** | Auto-generated debug build artifacts |
| ├── **Core/** | Compiled Core build outputs |
| ├── **Drivers/STM32F4xx_HAL_Driver/** | HAL driver compiled outputs |
| ├── *makefile* | Build rules |
| ├── *objects.list* | Object file listing |
| ├── *objects.mk* | Auto-generated dependency rules |
| ├── *sources.mk* | Auto-generated source list |
| ├── *theLast.elf* | Compiled ELF binary |
| ├── *theLast.list* | Assembly listing |
| └── *theLast.map* | Memory map of the build |
| **Drivers/** | Driver files used by the application |
| **README.md** | Main project documentation |
| **STM32F401CCUX_FLASH.ld** | Linker script for STM32F401 |
| **theLast Debug.launch** | Debug launch configuration |
| **theLast.ioc** | STM32CubeMX configuration file |


---

## 🛠 Hardware Requirements (textual list for clarity)
- STM32F401 / STM32F4 Board — Main controller  
- MFRC522 RFID Reader — Reads card UID (SPI)  
- SSD1306 128×64 OLED — UI (I2C)  
- Potentiometer — Candidate selection (ADC)  
- Push Button — Vote confirmation  
- Buzzer — Audio alerts  
- LED on PC13 — RFID activity

---

## 🔌 Pin Configuration (Used in Code)
To stay GitHub-friendly and visual, here's the pin mapping shown as a Mermaid flow/association diagram.

```mermaid
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
