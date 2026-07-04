# Event Board: RTC-Driven Message Display System

An automated, time-triggered messaging and environmental monitoring system built on the **ARM7 LPC2148 micro-controller**. The system dynamically switches between displaying scheduled event announcements with a smooth scrolling mechanism and an idle dashboard monitoring live room parameters. Secure management access is guarded via a physical bypass switch and a matrix keypad password authentication layer.

## 🚀 Key Features

* **Real-Time Automated Scheduling:** Uses the LPC2148's internal Real-Time Clock (RTC) to accurately trigger up to 10 distinct schedules.
* **Smart LCD Streaming Engine:** Features a dynamic text-shifting routine on a 16x2 character display to cleanly stream multi-line sentences (up to 80 characters) without truncation.
* **Environmental Telemetry:** Leverages an on-chip Successive Approximation ADC to acquire real-time analog data from an LM35 temperature sensor during system idle periods.
* **Dual-State Visual Indicators:**
  * **Active Mode:** Green LED illuminates while a scheduled bulletin is broadcasting.
  * **Idle Mode:** Red LED illuminates when flashing live system parameters (Time, Date, and Temperature).
* **Secure Admin Controls:** Includes a dedicated physical toggle switch alongside a password-protected $4 \times 4$ matrix keypad. Authorized access unlocks an editor to recalibrate system time or toggle specific schedules on/off for the day.
* **Acoustic Alerts:** An active piezo buzzer provides tactile feedback for keypresses and triggers alarms for incorrect credential entries.

---

## 🛠️ System Architecture

### Hardware Components
* **Micro-controller:** NXP LPC2148 (ARM7TDMI-S)
* **Display:** 16x2 Character LCD (HD44780 compliant)
* **Transducers:** LM35 Precision Centigrade Temperature Sensor
* **User Input:** $4 \times 4$ Matrix Keypad & SPST Slide Toggle Switch
* **Signaling:** Red & Green Low-Current LEDs, 5V Magnetic Buzzer

### Software Stack
* **Development IDE:** Keil uVision IDE v5
* **Compiler:** ARM Compiler v5 / Embedded C
* **Flashing Tool:** Flash Magic Utility (ISP over UART0)

---

## 📂 Repository Structure

├── drivers/               # Peripheral initialization routines
│   ├── lpc2148_rtc.c      # On-chip RTC control & configuration
│   ├── lpc2148_adc.c      # Analog-to-digital conversions for LM35
│   ├── lcd_16x2.c         # LCD initialization, commands, and custom scrolling loops
│   └── keypad.c           # Matrix row-scanning & debouncing logic
├── src/
│   ├── main.c             # Core system state machine & execution loop
│   └── admin.c            # Password verification & menu handling
└── README.md              # Documentation
