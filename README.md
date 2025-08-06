# Inductive Sensor Logger with ESP32 and PMI40-F90-IU-IO-V15

A compact ESP32-based data acquisition and logging system using the Pepperl+Fuchs PMI40-F90-IU-IO-V15 inductive positioning sensor. Designed for standalone operation with web interface, SPIFFS storage, and analog signal processing.

---

## 📦 Project Overview

This project integrates:
- **ESP32 DevKitC** microcontroller
- **PMI40-F90-IU-IO-V15** inductive analog sensor (0–40 mm range)
- Onboard analog signal reading and processing (via ADC)
- Data logging to internal SPIFFS filesystem
- Web-based interface for real-time data access
- External 5V power supply via connector

---

## ⚙️ Hardware Features

- **Sensor**: Pepperl+Fuchs PMI40-F90-IU-IO-V15  
  - IO-Link capable (used in analog mode)
  - Outputs: 4–20 mA or 0–10 V (configurable)
- **Microcontroller**: ESP32 DevKitC  
  - 12-bit ADC input
  - USB serial and 5V power input
- **Power**: External 5V supply via `Conn_01x02` connector  
  - PWR_FLAG used in KiCad schematic to indicate powered nets
- **PCB**: Custom layout with connector-based sensor input and USB/debug interface

---

## 🧰 Firmware Features

- ESP-IDF based C firmware
- ADC read of analog sensor values
- Periodic logging to SPIFFS as CSV
- Web interface:
  - Real-time sensor value display
  - Log viewer + download option
  - File management

---

## 🛠️ Schematic Summary

Power input via `Conn_01x02`:
- `+5V` and `GND` nets marked with `PWR_FLAG` for ERC compliance.
- Sensor analog output connected to ESP32 ADC input (e.g. GPIO34).

Pin 1 → +5V → ESP32 [5V/VIN]
Pin 2 → GND → ESP32 [GND]

---

## 📝 Development Timeline

| Week | Milestone |
|------|-----------|
| 1 | Parts ordered, project kickoff |
| 2–3 | Mechanical housing & 3D print |
| 4 | Soldering prototype PCB |
| 5–6 | Firmware dev: ADC, SPIFFS, web UI |
| 7 | System integration |
| 8–9 | Testing and tuning |
| 10 | Final delivery and documentation |

---

## 📁 File Structure (Example)

├── firmware/
│ ├── main/
│ └── components/
├── hardware/
│ ├── schematic.kicad_sch
│ └── pcb.kicad_pcb
├── logs/
│ └── sensor-log.csv
└── README.md
---

## 📎 Notes

- Ensure analog output on PMI40 is configured for **0–10 V** or **0–5 V** range depending on ESP32 ADC input voltage tolerance.
- Total current from IO-Link Master or supply must remain within allowed limits.
- Consider voltage divider or op-amp buffer if scaling signal.

---
