# ArcHound — Hardware, Schematics & Design Files

Community packaging as **ArcHound**. Files originate from ElectroPup (reubenstr).

Complete index of electronics, CAD, BOM, and datasheets included in this fork
(same files as upstream).

## KiCad PCBs & schematics

Designed in **KiCad v8**. Fabrication notes: JLCPCB. Custom footprints may need
[reubenstr/kicad-libraries](https://github.com/reubenstr/kicad-libraries).

| Board | Schematic | PCB | Gerbers / notes |
|-------|-----------|-----|-----------------|
| **Power Carrier** | [`pcbs/power_carrier/power_carrier.kicad_sch`](../pcbs/power_carrier/power_carrier.kicad_sch) | [`power_carrier.kicad_pcb`](../pcbs/power_carrier/power_carrier.kicad_pcb) | [`pcbs/power_carrier/gerbers/`](../pcbs/power_carrier/gerbers/) |
| **Auxiliary Board** | [`pcbs/auxiliary-board/auxiliary-board.kicad_sch`](../pcbs/auxiliary-board/auxiliary-board.kicad_sch) | [`auxiliary-board.kicad_pcb`](../pcbs/auxiliary-board/auxiliary-board.kicad_pcb) | see board folder + backups |
| Graphic footprint | — | — | [`pcbs/electroPup-graphic.kicad_mod`](../pcbs/electroPup-graphic.kicad_mod) |

Board overview: [`pcbs/README.md`](../pcbs/README.md)

### Power Carrier (summary)

- Main on/off power switch  
- Motor power headers  
- Four CAN networks (one per leg; jumpers can merge front/rear pairs)  

### Auxiliary Board (optional)

- STM32F401 Black Pill, LCD, buzzer, NeoPixels, RC servo, button  
- RPi breakouts: BNO055 IMU, SBUS, I2S, contact GPIO  

## Block diagrams & design sources

| File | Description |
|------|-------------|
| [`docs/block-diagram.drawio`](block-diagram.drawio) | System block diagram (Draw.io) |
| [`docs/sources/gamepad-controls.drawio`](sources/gamepad-controls.drawio) | Gamepad mapping |
| [`docs/sources/motor-layout.drawio`](sources/motor-layout.drawio) | Motor layout |
| [`images/archound-block-diagram.png`](../images/archound-block-diagram.png) | Rendered architecture diagram |
| [`images/archound-power-carrier-v1-render.png`](../images/archound-power-carrier-v1-render.png) | Power Carrier render |
| [`images/archound-auxiliary-board-v1-render.png`](../images/archound-auxiliary-board-v1-render.png) | Aux board render |

## CAN bus reference schematics / datasheets

| File | Description |
|------|-------------|
| [`docs/can/2-CH-CAN-HAT-Schematic.pdf`](can/2-CH-CAN-HAT-Schematic.pdf) | Waveshare 2-CH CAN HAT schematic |
| [`docs/can/2-CH_CAN_HAT_drawing.zip`](can/2-CH_CAN_HAT_drawing.zip) | Mechanical drawings |
| [`docs/can/MCP2515.pdf`](can/MCP2515.pdf) | MCP2515 datasheet |
| [`docs/can/sn65hvd230.pdf`](can/sn65hvd230.pdf) | SN65HVD230 datasheet |
| [`docs/can/RPI-GPIO-Pinout-Diagram.png`](can/RPI-GPIO-Pinout-Diagram.png) | RPi GPIO pinout |

## Motors & power

| File | Description |
|------|-------------|
| [`docs/motors/lingkong-motor-manual.pdf`](motors/lingkong-motor-manual.pdf) | LingKong motor manual |
| [`docs/motors/lingkong-motor-communications.pdf`](motors/lingkong-motor-communications.pdf) | CAN communications |
| [`docs/motors/MG4010E-dimensions.webp`](motors/MG4010E-dimensions.webp) | Dimensions |
| [`docs/motors/MG4010E-specifications.webp`](motors/MG4010E-specifications.webp) | Specs |
| [`docs/datasheets/SCW12-spec.pdf`](datasheets/SCW12-spec.pdf) | SCW12 DC-DC spec |
| [`docs/battery/`](battery/) | Battery build notes & photos |

## BOM, prints, calcs (LibreOffice)

| File | Description |
|------|-------------|
| [`docs/bom.ods`](bom.ods) | Bill of materials |
| [`docs/3d-prints.ods`](3d-prints.ods) | 3D print list |
| [`docs/weights.ods`](weights.ods) | Mass budget |
| [`docs/power-calcs.ods`](power-calcs.ods) | Power calculations |
| [`docs/calcs.ods`](calcs.ods) | Misc calculations |

## CAD / 3D prints

| Path | Description |
|------|-------------|
| [`cad/3D/v1/*.stl`](../cad/3D/v1/) | Printable STL parts |
| [`cad/3D/v1/assembly-v20.step`](../cad/3D/v1/assembly-v20.step) | STEP assembly |
| [`cad/3D/assembly-v20.step`](../cad/3D/assembly-v20.step) | STEP assembly (root) |
| [`cad/2D/electropup.dwg`](../cad/2D/electropup.dwg) | 2D DWG |
| Onshape links | See main [README](../README.md#cad--3d-prints) |

## Firmware (aux board)

| Path | Description |
|------|-------------|
| [`firmware/aux/`](../firmware/aux/) | PlatformIO project for STM32 Black Pill |

## Setup guide

See [`docs/setup.md`](setup.md) for Ubuntu + Raspberry Pi + motor setup.
