# RFID Voting System – STM32F401 + MFRC522 + SSD1306

A fully working **RFID-based electronic voting system** developed using **STM32CubeIDE**,  
**MFRC522 RFID Reader (SPI)**, **SSD1306 OLED Display (I2C – register level)**,  
**Potentiometer (ADC)** for selecting candidates, and **Push Button + Buzzer** for UI controls.

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
