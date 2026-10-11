# Starbie — Half Life Week 1 KiCad draft

This project is based on SharKingStudios/Starbie's Week 1 guide and the supplied Week 1 Care Package.

## Files
- `Starbie.kicad_pro` — KiCad project
- `Starbie.kicad_sch` — editable schematic draft
- `Starbie.kicad_pcb` — editable PCB placement/net draft
- `Imported Parts.pretty/` — supplied OLED, MPU6050 and XIAO footprints
- `StarbieParts.pretty/` — helper footprints for the DHT11 header and buttons
- `Seeed_Studio_XIAO_Series.kicad_sym` — supplied Seeed symbol library
- `3D Models/` — supplied STEP models

## Pin/net map
| Function | XIAO ESP32-C3 label | GPIO | PCB net |
|---|---|---:|---|
| OLED SDA + MPU6050 SDA | D4 | GPIO6 | `I2C_SDA` |
| OLED SCL + MPU6050 SCL | D5 | GPIO7 | `I2C_SCL` |
| DHT11 data | D1 | GPIO3 | `DHT_DATA` |
| Button 1 | D2 | GPIO4 | `BUTTON_1` |
| Button 2 | D3 | GPIO5 | `BUTTON_2` |
| Power | 3V3 | — | `3V3` |
| Ground | GND | — | `GND` |

<img width="643" height="519" alt="Starbie pcb 2" src="https://github.com/user-attachments/assets/d1facf39-8ce3-4fc9-8ac6-d51a68db5f65" />

The OLED footprint uses the care-package pad order: 1=GND, 2=VDD, 3=SCL, 4=SDA.
The MPU6050 module footprint is mapped as 1=VCC, 2=GND, 3=SCL, 4=SDA; pads 5–8 are left unconnected.
The DHT11 header is mapped 1=3V3, 2=DATA, 3=NC, 4=GND.
Buttons are modeled as generic 2-pad through-hole switches; verify that this matches the actual switch style you plan to use.

## IMPORTANT: current status
This is an **editable first-pass draft**, not a fabrication-ready board. The PCB footprints are placed and nets are assigned, but the copper tracks have **not** been routed, no ground pour has been added, and DRC has not been run in KiCad. Do not order a PCB from this draft yet.

## Next steps in KiCad
1. Open `Starbie.kicad_pro`.
2. Open the schematic and check that the labels are attached to the intended pins.
3. Open PCB Editor and run **Update PCB from Schematic** if needed.
4. Finish arranging footprints, route every airwire on F.Cu/B.Cu, add a GND zone if desired, and refill zones.
5. Run **Inspect → Design Rules Checker** and resolve all errors/unconnected nets.
6. Save, then export Gerbers and drill files only after the board is fully checked.

Reference: https://github.com/SharKingStudios/Starbie/blob/main/Week%201%20Guide.md
