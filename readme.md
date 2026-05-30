# FMCW3 Hardware Design

Custom 6-layer FPGA-based FMCW radar platform designed in KiCad for high-speed radar acquisition, RF processing, and FPGA DSP applications.

The project integrates:

- RF transmitter and dual receiver chains
- ADL5802 mixer stage
- ADA4940 IF signal conditioning
- LTC2292 high-speed ADC
- Artix-7 FPGA processing
- FT2232H USB FIFO streaming
- Multi-rail low-noise power architecture

<img width="2017" height="1039" alt="Image" src="https://github.com/user-attachments/assets/9d192d24-a084-4770-912a-be3e354d8ac5" />
<img width="1705" height="927" alt="Image" src="https://github.com/user-attachments/assets/b9702ea5-ba15-4ebc-af8d-9178bafbd167" />
<img width="2070" height="1128" alt="Image" src="https://github.com/user-attachments/assets/f70d1eda-28ec-47b1-9dc3-914150351693" />
<img width="2070" height="1128" alt="Image" src="https://github.com/user-attachments/assets/e5d4a81b-602c-433c-af42-01f68299b019" />
<img width="2070" height="1128" alt="Image" src="https://github.com/user-attachments/assets/fd771421-aff8-4e17-b73b-a0d71dcc0cff" />
<img width="2070" height="1128" alt="Image" src="https://github.com/user-attachments/assets/82a9e850-7298-4cf8-b645-c6aa8c67f048" />
<img width="2070" height="1128" alt="Image" src="https://github.com/user-attachments/assets/534c3a9c-d7fe-4c5f-a111-9f096d9c7310" />

---

# Overview

FMCW3 is a custom 5.8 GHz FMCW radar hardware platform built around the Xilinx XC7A35T Artix-7 FPGA.

The board is designed for:

- FMCW radar experiments
- SAR imaging
- Doppler processing
- Phase analysis
- FPGA DSP development
- Radar algorithm research

---

# Main Features

## FPGA

- Xilinx XC7A35T-FTG256
- MicroBlaze soft-core support
- SPI Flash boot
- JTAG debugging
- SD card support
- Parallel ADC interface

## RF Front-End

- HMC431LP4 VCO
- Dual RX channels
- ADL5802 active mixer
- Differential IF architecture
- ADA4940 differential amplifiers

## ADC

- LTC2292 dual-channel ADC
- 12-bit parallel interface
- Differential analog inputs
- FPGA synchronous acquisition

## USB

- FT2232H
- FT245 synchronous FIFO mode
- USB Type-C
- High-speed radar data streaming

---

# 6-Layer PCB Design

The board is designed as a controlled impedance 6-layer RF PCB.

## RF Transmission Line Rules

### Single-Ended 50Ω

- JLCPCB:
  - 0.156 mm trace width
- CST Simulation:
  - 0.17 mm trace width

### Differential 50Ω

- 0.4 mm differential pair width/spacing

### USB Differential Pair

- Target impedance:
  - 90Ω differential
- 0.23 mm width
- 0.13 mm spacing

Results:
- ~100Ω on Oshpark
- ~85Ω on JLCPCB

Accepted as operational for USB HS routing.

---

# RF Layout Notes

- Ground pour kept at least:
  - 3× substrate height away from RF traces
- Via stitching placed:
  - ~1 mm beside RF traces
  - ~0.6 mm from trace edge
- LO path uses smooth bends for impedance continuity
- ADC and IF lengths matched for improved phase consistency
- RF clearances and differential routing optimized
- Differential RF routing corrected for proper 50Ω behavior

---

# KiCad Project Structure

```text
FMCW3/
├── fpga.kicad_sch
├── adc.kicad_sch
├── usb.kicad_sch
├── power.kicad_sch
├── mixer.kicad_sch
├── if.kicad_sch
├── tx.kicad_sch
├── rx.kicad_sch
├── fmcw3.kicad_sch
├── fmcw3.kicad_pcb
└── README.md
```

---

# Design Targets

| Parameter | Value |
|---|---|
| Radar Type | FMCW |
| Frequency | 5.8 GHz |
| FPGA | XC7A35T |
| ADC | LTC2292 |
| Mixer | ADL5802 |
| IF Amplifier | ADA4940 |
| USB Interface | FT2232H |
| PCB Stackup | 6 Layer |
| CAD Tool | KiCad 9 |

---

# Related Repositories

FPGA Firmware:
https://github.com/ckflight/FMCW3

Radar Software:
https://github.com/ckflight/FMCW_RADAR

https://github.com/ckflight/FMCW_RADAR_2v2

AI Radar Experiments:
https://github.com/ckflight/RADAR_24GHZ_NEURAL_NETWORK

---

# Author

Cenk KESKİN

---

# License

This project is licensed under the GNU General Public License v3.0 (GPLv3).

You are free to use, modify, and distribute this software under the terms of the GPLv3 license.

Any distributed modifications or derivative works must also be released under the same license and include source code.

For full license text:

https://www.gnu.org/licenses/gpl-3.0.html