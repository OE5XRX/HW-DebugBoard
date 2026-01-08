# HW-DebugBoard

Ein universelles Debug-Board für die OE5XRX-Modulplattform zur Entwicklung, Analyse und automatisierten Tests von Hardware-Modulen wie z. B. dem FM-Transceiver-Modul.

## Features

- USB-C + USB-Hub für:
  - Debug-STM32 (Firmwaretest)
  - ST-Link zur Programmierung
  - USB-Verbindung zum DUT
- Schnittstelle für genormte DUT-Module (2×10 Pin)
- INA226 für Strom- und Spannungsmessung
- OLED-Display und Taster zur Steuerung
- Erweiterbar durch GPIO, ADC, DAC, UARTs, I²C

## Projektstatus

🛠️ Derzeit in Schaltungsdesign-Phase (Schematic)

---

## ✅ To-do Liste (Schaltplan – Hierarchisch)

### 🔌 1. USB & USB-Hub (`usb_hub.sch`)
- [x] USB-C Buchse mit ESD-Schutz (TVS)
- [x] USB-Hub IC (z. B. FS1.1, TUSB2046B, GL850G)
- [x] Downstream-Port 1: Debug-STM32
- [x] Downstream-Port 2: ST-Link USB
- [x] Downstream-Port 3: DUT USB-Buchse
- [x] Taktquelle für USB-Hub (z. B. 12 MHz Quarz)
- [x] Serienwiderstände & Pull-Ups gemäß Datenblatt

### 🧠 2. Debug-Controller (`stm32.sch`)
- [x] STM32F302CBTx (LQFP-48)
- [x] Reset-Schaltung & ggf. Quarz
- [x] USB-Anbindung zum Hub
- [ ] GPIO-Zuweisungen:
  - [x] I²C für OLED & INA226
  - [ ] Taster (3×)
  - [x] DUT_RESET
  - [x] DUT_VCC_EN
  - [x] INA226_ALERT
- [x] Optional: eigene SWD-Schnittstelle

### 🧷 3. ST-Link Interface (`stlink.sch`)
- [ ] USB-A Buchse oder Pfostenleiste für ST-Link-Verbindung
- [ ] Mechanik zur Befestigung des ST-Link (z. B. Kabelbinderloch)
- [ ] Rückführung der SWD-Leitungen zum Board:
  - [ ] Wannenstecker zu DUT
  - [ ] Optional: Debug-STM32 Flashbarkeit

### 📟 4. Display & UI (`ui.sch`)
- [ ] SSD1306 OLED über I²C
- [ ] I²C Pull-Ups (z. B. 4.7 kΩ)
- [ ] 3 Taster mit Pull-Ups
- [ ] GPIO-Zuweisungen zu STM32

### ⚡ 5. DUT Power Control (`power_switch.sch`)
- [x] Lastschalter - TPS22917
  - [x] Enable via STM32
  - [x] Versorgung 5V
- [x] Abblock-Cs, evtl. Reverse Protection
- [ ] Spannungsversorgung zum DUT Header

### 📊 6. Strom-/Spannungsmessung (`ina226.sch`)
- [x] INA226 am I²C
- [x] Shunt-Widerstand (0.01 Ω, 1%, >0.5 W)
- [x] Alert-Signal an STM32
- [x] Serienschaltung im VCC Pfad zum DUT

### 🔁 7. DUT Interface Header (`hil_interface.sch`)
- [ ] SHF-110-01-L-D-RA (2×10)
- [ ] Finales Pinout definiert:
  - [ ] UART0 TX/RX
  - [ ] UART1 TX/RX
  - [ ] I²C SDA/SCL
  - [ ] ADC0, ADC1 mit AGND
  - [ ] DAC_OUT mit AGND
  - [ ] 3V3_SENSE
  - [ ] GND mehrfach verteilt
- [ ] ESD-Schutz und Serienwiderstände prüfen
- [ ] Labeling für Orientierung (z. B. Pin 1 Markierung)

### 🧩 8. Mechanik & DUT-Steckplatz (`dut_mech.sch`)
- [ ] Horizontale Buchse für DUT-Modul
- [ ] USB-Verbindung vom Hub zum DUT
- [ ] Mechanischer Bereich für Modul-Tausch
- [ ] Optional: Schraublöcher / Führung
- [ ] Platz für FM-Modul sicherstellen

### 🛠️ 9. Globales & Hilfsfunktionen (`globals.sch`)
- [ ] Power-Netze global (VBUS, 3V3, GND, etc.)
- [ ] Labeling (Silkscreen, Versionsnummer)
- [ ] I²C-Adressenübersicht
- [ ] Schutzbeschaltungen
- [ ] Board-ID optional

---

## 📄 License

This project is licensed under [CERN-OHL-S-2.0](https://choosealicense.com/licenses/cern-ohl-s-2.0/).

## 🧪 Badges

![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/OE5XRX/HW-DebugBoard/kibot-check.yaml?branch=main)<br>
![GitHub Release](https://img.shields.io/github/v/release/OE5XRX/HW-DebugBoard)<br>
![License: CERN-OHL-S](https://img.shields.io/badge/license-CERN--OHL--S--2.0-blue)<br>
![KiCad Supported](https://img.shields.io/badge/KiCad-supported-blue)<br>
![Project Type](https://img.shields.io/badge/type-hardware-red)<br>

## 📬 Contact

OE5XRX Amateur Radio Club<br>
🌐 https://oe5xrx.org<br>
✉️ info@oe5xrx.org<br>
