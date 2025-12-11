# RFID Voting System (STM32CubeIDE)

**Short description**  
An STM32F4-based RFID voting prototype that uses an MFRC522 (SPI) reader, an SSD1306 OLED (I2C implemented at register level), a potentiometer (ADC) for candidate selection and a push-button to confirm. Authorized UIDs are stored in the firmware; each authorized card may vote once per power-up. The UI is rendered on the SSD1306; votes are counted in RAM and shown on request.

---

## Repository contents (quick)
- `Core/`, `Drivers/`, `Debug/` — standard STM32CubeIDE project layout (generated `.ioc`, HAL files, linker script `STM32F401CCUX_FLASH.ld` present).
- `main.c` — high-level application (uses register-level I2C/ADC/GPIO + HAL SPI for MFRC522).
- `rc522.c/.h` — MFRC522 driver (expected to be in the project — required).
- README (this file)...

---

## Features
- MFRC522 RFID reader (HAL SPI) for voter identification.
- SSD1306 OLED display controlled via register-level I2C (PB6=SCL, PB7=SDA).
- Potentiometer on PA1 (ADC1_IN1) to choose candidate (three ranges).
- Push-button (PA0) to cast vote / show counts (long press behavior included).
- Buzzer on PB2 for audio feedback.
- LED on PC13 to indicate RFID read activity.
- Simple UI states: Welcome → Verify UID → Cast Vote → Vote Casted → Vote Counts.
- Runs on STM32F401 series (CubeMX-generated skeleton present).

---

## Quick start — clone & open

```bash
# clone repository
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
