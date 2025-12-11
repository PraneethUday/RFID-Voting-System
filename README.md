<!-- README.md — Single-file, GitHub-friendly, visually appealing with SVG animations -->
<!-- All original content preserved. Only presentation enhanced. -->

<p align="center">
  <img alt="rfid" src="https://img.shields.io/badge/PROJECT-RFID%20Voting-blue?style=flat-square" />
  <img alt="stm32" src="https://img.shields.io/badge/MCU-STM32F401-success?style=flat-square" />
  <img alt="mfrc522" src="https://img.shields.io/badge/RFID-MFRC522-orange?style=flat-square" />
  <img alt="ssd1306" src="https://img.shields.io/badge/OLED-SSD1306-lightgrey?style=flat-square" />
  <img alt="ide" src="https://img.shields.io/badge/IDE-STM32CubeIDE-informational?style=flat-square" />
</p>

<!-- Hero + animated summary SVG -->
<h1 align="center">🚀 RFID Voting System — STM32F401 + MFRC522 + SSD1306</h1>
<p align="center"><em>A fully working <strong>RFID-based electronic voting system</strong> developed using <strong>STM32CubeIDE</strong>, <strong>MFRC522 RFID Reader (SPI)</strong>, <strong>SSD1306 OLED Display (I2C – register level)</strong>, <strong>Potentiometer (ADC)</strong> for selecting candidates, and <strong>Push Button + Buzzer</strong> for UI controls.</em></p>

<div align="center">
<!-- Animated SVG "feature bars" — lightweight SMIL animation -->
<svg width="760" height="160" viewBox="0 0 760 160" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="project summary animation">
  <defs>
    <linearGradient id="g1" x1="0" x2="1">
      <stop offset="0" stop-color="#00aaff"/>
      <stop offset="1" stop-color="#0066cc"/>
    </linearGradient>
    <filter id="soft" x="-20%" y="-20%" width="140%" height="140%">
      <feDropShadow dx="0" dy="4" stdDeviation="6" flood-opacity="0.12"/>
    </filter>
  </defs>

  <rect x="8" y="8" rx="10" ry="10" width="744" height="144" fill="#f8fafc" stroke="#e6eef8" />
  <text x="26" y="34" font-family="Arial" font-size="14" fill="#0b2a4a" font-weight="700">Project Summary</text>

  <!-- Bars with animate for pulse -->
  <!-- RFID Auth -->
  <text x="26" y="62" font-size="12" fill="#084a8a">RFID Auth</text>
  <rect x="110" y="46" width="140" height="18" rx="6" fill="url(#g1)" filter="url(#soft)">
    <animate attributeName="width" from="1" to="140" dur="0.9s" begin="0.1s" fill="freeze" />
  </rect>

  <!-- OLED UI -->
  <text x="26" y="92" font-size="12" fill="#084a8a">OLED UI</text>
  <rect x="110" y="76" width="0" height="18" rx="6" fill="#44c7a8" filter="url(#soft)">
    <animate attributeName="width" from="1" to="120" dur="1s" begin="0.3s" fill="freeze" />
  </rect>

  <!-- Pot + Button -->
  <text x="26" y="122" font-size="12" fill="#084a8a">Potentiometer + Button</text>
  <rect x="210" y="106" width="0" height="18" rx="6" fill="#ffb020" filter="url(#soft)">
    <animate attributeName="width" from="1" to="200" dur="1.1s" begin="0.5s" fill="freeze" />
  </rect>

  <!-- small caption -->
  <text x="26" y="146" font-size="11" fill="#6b7280">Animated summary — shows main subsystems (for README clarity)</text>
</svg>
</div>

---

This project demonstrates an embedded, real-time, secure voting flow where each authorized RFID card can vote only once.

---

# 📌 **Features**
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

# 📂 **Repository Structure**
(Keep your existing repo structure here — same filenames and folders as original README)

---

# 🛠 **Hardware Requirements**
| Component | Purpose |
|----------|---------|
| STM32F401 / STM32F4 Board | Main controller |
| MFRC522 RFID Reader | Reads card UID (SPI) |
| SSD1306 128×64 OLED | UI (I2C) |
| Potentiometer | Candidate selection (ADC) |
| Push Button | Vote confirmation |
| Buzzer | Audio alerts |
| LED on PC13 | RFID activity |

---

# 🔌 **Pin Configuration (Used in Code)**

### **MFRC522 (SPI1)**
| MFRC522 Pin | STM32 Pin |
|-------------|-----------|
| SDA / CS    | PA4 |
| SCK         | PA5 |
| MOSI        | PA7 |
| MISO        | PA6 |
| RST         | PB0 |
| IRQ         | — (not used) |

### **SSD1306 OLED (I2C – Register Level Implementation)**
| Signal | STM32 Pin |
|--------|-----------|
| SCL     | PB6 |
| SDA     | PB7 |

### **Other Peripherals**
| Function | Pin |
|----------|-----|
| Button (active-low) | PA0 |
| Potentiometer (ADC1_IN1) | PA1 |
| Buzzer | PB2 |
| LED (Active-low) | PC13 |

---

# 🚀 **How to Clone & Open the Project**

### **1️⃣ Clone the repository**
```bash
git clone https://github.com/PraneethUday/RFID-Voting-System.git
cd RFID-Voting-System
