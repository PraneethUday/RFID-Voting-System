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

## ✨ Visual Snapshot (animated)

<!-- Animated summary SVG — feature bars -->
<p align="center">
<svg width="760" height="160" viewBox="0 0 760 160" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Project visual summary">
  <rect x="8" y="8" rx="10" ry="10" width="744" height="144" fill="#ffffff" stroke="#e6eef8" />
  <text x="26" y="34" font-family="Arial" font-size="14" fill="#0b2a4a" font-weight="700">Project Summary</text>

  <text x="26" y="62" font-size="12" fill="#334155">RFID Auth</text>
  <rect x="120" y="48" width="0" height="16" rx="6" fill="#0ea5e9">
    <animate attributeName="width" from="0" to="260" dur="0.9s" begin="0.1s" fill="freeze" />
  </rect>

  <text x="26" y="92" font-size="12" fill="#334155">OLED UI</text>
  <rect x="120" y="78" width="0" height="16" rx="6" fill="#10b981">
    <animate attributeName="width" from="0" to="200" dur="1s" begin="0.25s" fill="freeze" />
  </rect>

  <text x="26" y="122" font-size="12" fill="#334155">Potentiometer + Button</text>
  <rect x="200" y="108" width="0" height="16" rx="6" fill="#f59e0b">
    <animate attributeName="width" from="0" to="300" dur="1.1s" begin="0.4s" fill="freeze" />
  </rect>
</svg>
</p>

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

## 📈 Data Visualizations (SVG + small legends)
Below are a few visual components to replace ordinary tables — still accessible (text is included) and GitHub-compatible.

### 1) Feature Coverage (animated bars)
<p align="center">
<svg width="720" height="140" viewBox="0 0 720 140" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Feature coverage bars">
  <rect x="6" y="6" width="708" height="128" rx="8" fill="#fff" stroke="#e6eef8"/>
  <text x="18" y="28" font-family="Arial" font-size="13" fill="#0b2a4a" font-weight="700">Feature Coverage</text>

  <text x="18" y="54" font-size="11" fill="#334155">RFID Auth</text>
  <rect x="110" y="42" width="0" height="12" rx="6" fill="#0ea5e9">
    <animate attributeName="width" from="0" to="420" dur="1s" begin="0.05s" fill="freeze"/>
  </rect>

  <text x="18" y="78" font-size="11" fill="#334155">OLED UI</text>
  <rect x="110" y="66" width="0" height="12" rx="6" fill="#10b981">
    <animate attributeName="width" from="0" to="360" dur="1s" begin="0.15s" fill="freeze"/>
  </rect>

  <text x="18" y="102" font-size="11" fill="#334155">Pot/Button</text>
  <rect x="110" y="90" width="0" height="12" rx="6" fill="#f59e0b">
    <animate attributeName="width" from="0" to="480" dur="1s" begin="0.25s" fill="freeze"/>
  </rect>
</svg>
</p>

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
(Keep your existing repo structure here — same filenames and folders as original README)

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
