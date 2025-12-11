RFID Voting System (STM32CubeIDE)

Short description
An STM32F4-based RFID voting prototype that uses an MFRC522 (SPI) reader, an SSD1306 OLED (I2C implemented at register level), a potentiometer (ADC) for candidate selection and a push-button to confirm. Authorized UIDs are stored in the firmware; each authorized card may vote once per power-up. The UI is rendered on the SSD1306; votes are counted in RAM and shown on request.

Repository contents (quick)

Core/, Drivers/, Debug/ — standard STM32CubeIDE project layout (generated .ioc, HAL files, linker script STM32F401CCUX_FLASH.ld present).

main.c — high-level application (uses register-level I2C/ADC/GPIO + HAL SPI for MFRC522).

rc522.c/.h — MFRC522 driver (expected to be in the project — required).

README (this file)...

Features

MFRC522 RFID reader (HAL SPI) for voter identification.

SSD1306 OLED display controlled via register-level I2C (PB6=SCL, PB7=SDA).

Potentiometer on PA1 (ADC1_IN1) to choose candidate (three ranges).

Push-button (PA0) to cast vote / show counts (long press behavior included).

Buzzer on PB2 for audio feedback.

LED on PC13 to indicate RFID read activity.

Simple UI states: Welcome → Verify UID → Cast Vote → Vote Casted → Vote Counts.

Runs on STM32F401 series (CubeMX-generated skeleton present).

Quick start — clone & open
# clone repository
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>

Open in STM32CubeIDE

Launch STM32CubeIDE.

File → Open Projects from File System... → choose the repo folder and select the project (it should contain the .ioc file / Core/ etc.).

Alternatively, open the .ioc file directly (double-click) to import the CubeMX configuration.

Let CubeIDE index the project. If prompted, allow it to regenerate code from the .ioc (do so if you changed peripheral settings).

Build & flash

Select the project in Project Explorer.

Project → Build Project (or the build icon).

Connect your ST-LINK (or other programmer) to the target board (e.g., Nucleo/Discovery or custom board using STM32F401).

Use Run → Debug or Run As → STM32 Cortex-M C/C++ Application to flash via ST-LINK (CubeIDE will use ST-LINK under the hood).

Or use STM32CubeProgrammer / st-flash / openocd as you prefer.

Hardware wiring / pin mapping (as used in main.c)

MCU target: STM32F401 (check STM32F401CCUX_FLASH.ld — adjust if using different variant).

Function	MCU Pin	Notes / Signal
LED (active-low)	PC13	External LED (PC13 high = OFF)
Button (active-low)	PA0	External push button, internal pull-up enabled
Potentiometer (ADC)	PA1 (ADC1_IN1)	Read selection (12-bit ADC)
SPI1 - MFRC522	PA4 = CS	MFRC522 NSS (chip select) — idle HIGH
	PA5 = SCK	SPI1_SCK
	PA6 = MISO	SPI1_MISO
	PA7 = MOSI	SPI1_MOSI
MFRC522 RST	PB0	Reset pin (active low if wired that way)
Buzzer	PB2	Simple GPIO drive for buzzer
SSD1306 (I2C)	PB6 = SCL	I2C implemented at register level (AF4)
	PB7 = SDA	I2C SDA

NOTE: The MFRC522 library used in the project expects HAL SPI1 to be initialized. Confirm that your board physically connects MFRC522 SPI pins to PA4/PA5/PA6/PA7 or change the CubeMX SPI pins accordingly.

Software dependencies

STM32CubeIDE (or CubeMX + preferred toolchain)

STM32CubeF4 HAL (project already includes HAL code)

MFRC522 driver (rc522.c / rc522.h) — make sure these files are present in the project and reference hspi1.

No external SSD1306 library required — display driver code is register-level in main.c.

Configurations you may want to change

Authorized UIDs: auth_uids array in main.c — update with your card UIDs (5 bytes each).

ADC thresholds: adc_thresh_low and adc_thresh_high — change to tune pot ranges for 3 candidates.

Vote persistence: votes and voted_flags[] are stored in RAM — they reset on power cycle. If you want non-volatile storage, integrate EEPROM/FLASH write logic.

MCU / Clock: SystemClock_Config() is CubeMX-style; verify clock settings match your board.

How to get a UID (quick)

Use a simple MFRC522 UID read example (or run the project and present RFID card). Authorized UIDs are printed on the OLED in show_verified_with_uid() and show_invalid_with_uid() with format UID:XX XX XX XX XX.

Usage (runtime)

Power the board. OLED shows WELCOME / RFID VOTING SYSTEM.

Present an RFID card/tag:

If UID matches auth_uids[] and the card hasn't voted, device will beep once and show VOTER ID VERIFIED.

If not authorized, device will beep 3 times and show VOTER ID INVALID.

If the authorized UID has already voted (in RAM), the OLED shows VOTED ALREADY.

After verification, the UI moves to CASTE VOTE screen. Turn the potentiometer to move selection between COMMUNIST, CONGRESS, BJP.

Press and release the button (short press) to cast the vote (when verified). A vote confirmation screen appears briefly.

Long-press (from Welcome screen) shows vote counts for all parties.

LED on PC13 indicates a successful RFID detection while the internal LED timer (MIN_LED_ON_MS) is active.

Troubleshooting

OLED shows nothing

Ensure PB6/PB7 wired correctly and pull-ups present (we enable internal pull-up).

Check SSD1306_ADDR_7BIT (0x3C typical). Confirm your OLED address.

Use an I2C scanner (on PC) or temporarily add debug prints (UART) to ensure I2C code runs.

RFID not detected

Check MFRC522 connections: CS(SS) to PA4, SCK/MOSI/MISO to PA5/PA7/PA6.

Verify rc522.c uses hspi1 and MX_SPI1_Init() ran successfully.

Ensure MFRC522_Init() is called (it is in main()).

ADC selection jitter

Add small averaging in read_pot_adc_register() if pot is noisy; adjust adc_thresh_*.

Button not working

Check PA0 wiring and confirm active-low switch and pull-up configuration.

Build errors about missing rc522.c/.h or HAL files

Add / verify rc522.c and rc522.h are included in the project (they must use hspi1).

Make sure CubeIDE generated files are present (stm32f4xx_hal_*, startup files, linker script).

Project targets different STM32 variant

If you use a different MCU, update the CubeMX .ioc and pin mapping (and re-generate).

Important notes & limitations

Votes and voted_flags[] are only in RAM — rebooting clears them.

The project uses register-level I2C and ADC code for learning/compactness; be careful if you change system clocks or peripheral clocks — the constants used assume typical CubeMX settings (PCLK1 ~ 42 MHz in this code).

EXTI0_IRQHandler is present but contains dummy code; if you enable EXTI on PA0 make sure the ISR and NVIC priorities align with your CubeMX settings.

This code does not implement security beyond simple UID checking — do not use it for real-world election systems.

Customize authorized users

Open main.c and edit:

static const uint8_t auth_uids[][5] = {
    { 0x73, 0x91, 0xB1, 0x28, 0x7B },
    ...
};


Replace each { ... } with your card UID bytes (in hex). Rebuild and flash.

License

This project is provided as-is. Add a license file if you want (e.g., MIT LICENSE).

Acknowledgements / Credits

MFRC522 driver (community implementations) — ensure you attribute if using third-party code.

SSD1306 font and simple driver integrated into main.c.

Example git instructions you can paste
# clone
git clone https://github.com/<your-username>/<repo>.git
cd <repo>

# open in STM32CubeIDE:
# File -> Open Projects from File System... -> Browse to this repo folder

# build inside CubeIDE, then flash via ST-LINK
