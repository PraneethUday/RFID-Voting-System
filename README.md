<!-- README.md — Creative GitHub-friendly design (single file) -->

<p align="center">
  <img alt="project" src="https://img.shields.io/badge/PROJECT-RFID%20Voting-blue?style=flat-square" />
  <img alt="mcu" src="https://img.shields.io/badge/MCU-STM32F401-success?style=flat-square" />
  <img alt="rfid" src="https://img.shields.io/badge/RFID-MFRC522-orange?style=flat-square" />
  <img alt="oled" src="https://img.shields.io/badge/OLED-SSD1306-lightgrey?style=flat-square" />
  <img alt="ide" src="https://img.shields.io/badge/IDE-STM32CubeIDE-informational?style=flat-square" />
</p>

# 🚀 RFID Voting System — STM32F401 + MFRC522 + SSD1306

*A fully working **RFID-based electronic voting system** developed using **STM32CubeIDE**, **MFRC522 (SPI)**, **SSD1306 OLED (I2C — register-level)**, a potentiometer (ADC) to choose candidates, plus a push button and buzzer for the UI. Each authorized RFID card can vote only once.*

---

## 🎛 Hero — Control Grid (compact UI illustration)
<p align="center">
<!-- Button-grid style SVG (inspired by your example) -->
<svg width="420" height="180" viewBox="0 0 420 180" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="control grid">
  <rect x="0" y="0" width="420" height="180" fill="transparent" />
  <!-- central column -->
  <g transform="translate(160,18)">
    <!-- top row -->
    <g transform="translate(40,0)">
      <rect x="-28" y="4" rx="10" ry="10" width="56" height="56" fill="#0b1220" stroke="#2b3744" />
      <text x="-6" y="36" fill="#bfe3ff" font-size="18" font-family="Arial">▲</text>
    </g>
    <g transform="translate(120,0)">
      <rect x="-28" y="4" rx="10" ry="10" width="56" height="56" fill="#0b1220" stroke="#2b3744" />
      <text x="-7" y="36" fill="#bfe3ff" font-size="20" font-family="Arial">🔍</text>
    </g>

    <!-- middle -->
    <g transform="translate(0,66)">
      <rect x="-28" y="0" rx="12" ry="12" width="56" height="56" fill="#0b1220" stroke="#2b3744" />
      <text x="-10" y="36" fill="#bfe3ff" font-size="20" font-family="Arial">◀</text>
    </g>

    <g transform="translate(80,66)">
      <rect x="-28" y="0" rx="12" ry="12" width="56" height="56" fill="#0b1220" stroke="#2b3744" />
      <circle cx="0" cy="28" r="10" fill="#1f2937" stroke="#3b4654"/>
      <path d="M -6 28 L 6 28 M 0 22 L 0 34" stroke="#9ad3ff" stroke-width="2" stroke-linecap="round"/>
    </g>

    <g transform="translate(160,66)">
      <rect x="-28" y="0" rx="12" ry="12" width="56" height="56" fill="#0b1220" stroke="#2b3744" />
      <text x="-4" y="36" fill="#bfe3ff" font-size="20" font-family="Arial">▶</text>
    </g>

    <!-- bottom -->
    <g transform="translate(40,132)">
      <rect x="-28" y="0" rx="10" ry="10" width="56" height="36" fill="#0b1220" stroke="#2b3744" />
      <text x="-8" y="24" fill="#bfe3ff" font-size="18" font-family="Arial">▼</text>
    </g>

    <g transform="translate(120,132)">
      <rect x="-28" y="0" rx="10" ry="10" width="56" height="36" fill="#0b1220" stroke="#2b3744" />
      <text x="-10" y="24" fill="#bfe3ff" font-size="18" font-family="Arial">🔎</text>
    </g>
  </g>

  <!-- label -->
  <text x="16" y="24" font-family="Arial" font-size="13" fill="#0b2a4a" font-weight="700">UI Control Grid — Pot / Button / Buzzer / OLED</text>
  <text x="16" y="44" font-family="Arial" font-size="11" fill="#374151">Compact visual of input controls on the candidate-selection UI</text>
</svg>
</p>

---

# 📌 Features (visual card)
<p align="center">
<svg width="860" height="130" viewBox="0 0 860 130" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="features card">
  <rect x="8" y="8" width="844" height="114" rx="10" fill="#ffffff" stroke="#e6eef8"/>
  <text x="24" y="34" font-family="Arial" font-size="18" font-weight="700" fill="#0b2a4a">Features</text>

  <g font-family="Arial" font-size="12" fill="#0b2a4a">
    <text x="28" y="58">✔ RFID-based voter authentication using MFRC522</text>
    <text x="28" y="78">✔ OLED UI using SSD1306 (Register-level I2C implementation)</text>
    <text x="28" y="98">✔ Potentiometer for candidate selection (ADC on PA1) — Push-button confirmation</text>
  </g>
</svg>
</p>

---

## 📈 Visual Data — Animated Bars & Donut (GitHub-safe SVG)

### Feature Coverage (bars)
<p align="center">
<svg width="720" height="140" viewBox="0 0 720 140" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="feature coverage bars">
  <rect x="6" y="6" width="708" height="128" rx="8" fill="#fff" stroke="#e6eef8"/>
  <text x="18" y="28" font-family="Arial" font-size="13" fill="#0b2a4a" font-weight="700">Feature Coverage (visual)</text>

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

### Hardware Composition (donut/pie)
<p align="center">
<svg width="420" height="220" viewBox="0 0 420 220" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="hardware donut chart">
  <g transform="translate(210,110)">
    <circle r="100" fill="#fff" stroke="#e6eef8"/>
    <!-- slices are precomputed positions (visible via SMIL animation) -->
    <path d="M0 0 L 100 0 A 100 100 0 0 1 6.123e-15 100 Z" fill="#0ea5e9">
      <animate attributeName="d" dur="0.9s" from="M0 0 L0 0 Z" to="M0 0 L 100 0 A 100 100 0 0 1 6.123e-15 100 Z" fill="freeze" begin="0s"/>
    </path>
    <path d="M0 0 L 6.123e-15 100 A 100 100 0 0 1 -80.9 60 Z" fill="#10b981">
      <animate attributeName="d" dur="0.9s" from="M0 0 L0 0 Z" to="M0 0 L 6.123e-15 100 A 100 100 0 0 1 -80.9 60 Z" fill="freeze" begin="0.12s"/>
    </path>
    <path d="M0 0 L -80.9 60 A 100 100 0 0 1 -59 -81 Z" fill="#f59e0b">
      <animate attributeName="d" dur="0.9s" from="M0 0 L0 0 Z" to="M0 0 L -80.9 60 A 100 100 0 0 1 -59 -81 Z" fill="freeze" begin="0.24s"/>
    </path>
    <path d="M0 0 L -59 -81 A 100 100 0 0 1 100 0 Z" fill="#8b5cf6">
      <animate attributeName="d" dur="0.9s" from="M0 0 L0 0 Z" to="M0 0 L -59 -81 A 100 100 0 0 1 100 0 Z" fill="freeze" begin="0.36s"/>
    </path>
    <circle r="44" fill="#fff" stroke="#fff"/>
  </g>

  <g transform="translate(320,40)" font-family="Arial" font-size="11">
    <rect x="0" y="0" width="12" height="12" fill="#0ea5e9"/><text x="18" y="10">MCU — STM32F401</text>
    <rect x="0" y="20" width="12" height="12" fill="#10b981"/><text x="18" y="30">RFID — MFRC522</text>
    <rect x="0" y="40" width="12" height="12" fill="#f59e0b"/><text x="18" y="50">OLED — SSD1306</text>
    <rect x="0" y="60" width="12" height="12" fill="#8b5cf6"/><text x="18" y="70">Peripherals — Buttons/Buzzer/Pot</text>
  </g>
</svg>
</p>

> **Text fallback:** MCU 25% | RFID 25% | OLED 20% | Peripherals 30%.

---

## 📂 Repository Structure
(Keep your existing repo structure here — same filenames and folders as original README.)

---

## 🛠 Hardware Requirements (clean list)
- **STM32F401 / STM32F4 Board** — Main controller  
- **MFRC522 RFID Reader** — Reads card UID (SPI)  
- **SSD1306 128×64 OLED** — UI (I2C)  
- **Potentiometer** — Candidate selection (ADC)  
- **Push Button** — Vote confirmation  
- **Buzzer** — Audio alerts  
- **LED on PC13** — RFID activity

---

## 🔌 Pin Configuration (visual + Mermaid)
Below is a compact visual representation and a Mermaid diagram for exact mapping.

### Pin visual (compact)
<p align="center">
<svg width="760" height="110" viewBox="0 0 760 110" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="pin mapping">
  <rect x="8" y="8" width="744" height="94" rx="8" fill="#fff" stroke="#e6eef8"/>
  <text x="22" y="28" font-family="Arial" font-size="14" fill="#0b2a4a" font-weight="700">Pin Configuration (Used in Code)</text>

  <!-- left table items -->
  <text x="26" y="52" font-family="Arial" font-size="12" fill="#374151">MFRC522 (SPI1)</text>
  <text x="26" y="68" font-family="Arial" font-size="11" fill="#111827">SDA / CS → PA4  •  SCK → PA5  •  MOSI → PA7  •  MISO → PA6  •  RST → PB0</text>

  <text x="26" y="88" font-family="Arial" font-size="11" fill="#111827">IRQ → (not used)</text>

  <!-- right table items -->
  <text x="420" y="52" font-family="Arial" font-size="12" fill="#374151">SSD1306 (I2C)</text>
  <text x="420" y="68" font-family="Arial" font-size="11" fill="#111827">SCL → PB6  •  SDA → PB7</text>

  <text x="420" y="88" font-family="Arial" font-size="11" fill="#111827">Other: Button (PA0), Pot (PA1), Buzzer (PB2), LED (PC13)</text>
</svg>
</p>

### Pin mapping (Mermaid)
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
