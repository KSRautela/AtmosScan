# AtmosScan

AtmosScan is a multi-parametric air quality monitoring station designed to detect particulate matter (PM2.5), six distinct gases, and ambient climate data. Powered by the **Seeed Studio XIAO ESP32-C3**, the system utilizes analog multiplexing and logic level shifting to integrate a high-density sensor array into a compact, portable form factor.

---

## Hardware Specifications

### Core Processing & Connectivity
* **Microcontroller:** Seeed Studio XIAO ESP32-C3
* **Multiplexer:** 74HC4051 8:1 Analog Multiplexer (Sequential sampling of gas array)
* **Level Shifting:** Bidirectional Logic Level Shifter (3.3V to 5V translation)
* **Display:** I2C OLED Screen

### Sensor Suite
* **Particulate Matter:** PM2.5 Laser Scattering Sensor (UART)
* **Gas Array:** 6x Analog Gas Sensors (CO, $NO_2$, $NH_3$, $SO_2$, $O_3$, and VOCs)
* **Climate:** Temperature and Humidity Sensor (I2C)

### Power Management
* **Source:** 2S Li-ion Battery (7.4V nominal)
* **Regulation:** L7805 Linear Regulator (Providing stable 5V for sensor heaters and multiplexer)
* **Logic:** 3.3V supplied by the XIAO onboard regulator

---

## Circuit Architecture

The AtmosScan PCB manages three distinct signal types:
1.  **Analog Signals:** Six gas sensors feed into the 74HC4051. The XIAO ESP32-C3 selects the sensor via three digital pins (Address A, B, C) and reads the output through a single ADC pin (A0).
2.  **Digital (I2C):** The OLED screen.
3.  **Serial (UART):** The PM2.5 sensor communicates via high-speed serial, passed through the level shifter to match the MCU logic.

---

## Features

* **High-Density Sensing:** Monitoring 8 environmental parameters simultaneously.
* **Advanced Signal Routing:** Uses the 74HC4051 to expand the XIAO’s single ADC capability to handle the 6-gas array.
* **Voltage Compatibility:** Integrated level shifting ensures the 3.3V ESP32-C3 communicates safely with 5V sensors.
* **Mobile Operation:** Powered by a 2S battery configuration for field use and remote environmental tracking.

---

## Installation & Setup

1.  **Hardware Assembly:** Connect the 2S battery to the 7805 regulator input. 
2.  **Firmware:** Flash the provided Arduino/C++ code to the XIAO ESP32-C3.
3.  **Calibration:** Allow a 48-hour burn-in period for the gas sensors to achieve stable baseline readings.

---
![WhatsApp Image 2025-12-01 at 11 26 04](https://github.com/user-attachments/assets/e8cd18ee-29fe-4452-9ede-1dba5096f202)
