# ElectroPup (community fork)

<p align="center">
  <img src="images/electro-pup-standing.jpg" width="800" alt="ElectroPup standing">
</p>

**DIY 3D-printed quadruped** using low-cost BLDC actuators, Raspberry Pi 5, custom KiCad PCBs, and a Python control stack.

> **Upstream:** [reubenstr/ElectroPup](https://github.com/reubenstr/ElectroPup) by [reubenstr](https://github.com/reubenstr)  
> **This repo:** public community fork with clearer docs navigation — **all original CAD, schematics, firmware, and source files included**.  
> See [`NOTICE.md`](NOTICE.md) for attribution and license status.

[Kinematic poses (YouTube)](https://youtu.be/AJn_wCcWlwo) · [Walking / turning / strafing (YouTube)](https://youtu.be/YjTVNw8BXlM)

---

## Quick specs

| Item | Detail |
|------|--------|
| Compute | Raspberry Pi 5 |
| Actuators | 12× LingKong MG4010E-i10v3 BLDC (CAN) |
| Aux | Optional STM32 board + LCD, NeoPixels, buzzer |
| IMU | BNO055 (9-axis) |
| Battery | Custom 6S Li-Ion ~72 Wh |
| Mass | ~4.5 kg |
| Control | Python (non-ROS). ROS2 cousin: [Zuko](https://github.com/reubenstr/zuko) |

---

## Repository map

| Path | What’s inside |
|------|----------------|
| [`pcbs/`](pcbs/) | **KiCad schematics & PCBs** — Power Carrier + Auxiliary Board + gerbers |
| [`cad/`](cad/) | STLs, STEP assembly, 2D DWG |
| [`docs/`](docs/) | Setup guide, BOM, motor/CAN datasheets, Draw.io diagrams |
| [`docs/HARDWARE_AND_SCHEMATICS.md`](docs/HARDWARE_AND_SCHEMATICS.md) | **Index of every schematic / datasheet / BOM file** |
| [`firmware/aux/`](firmware/aux/) | PlatformIO firmware for aux STM32 |
| [`src/`](src/) | Python control, UI (Expo/React Native), MuJoCo sim |
| [`images/`](images/) | Photos, renders, UI screenshots |
| [`videos/`](videos/) | Demo clips |

Original upstream README (verbatim copy): [`docs/README_UPSTREAM.md`](docs/README_UPSTREAM.md)

---

## Electronics & schematics

Open these first if you want to build the boards:

1. **Index:** [`docs/HARDWARE_AND_SCHEMATICS.md`](docs/HARDWARE_AND_SCHEMATICS.md)
2. **Power Carrier schematic:** [`pcbs/power_carrier/power_carrier.kicad_sch`](pcbs/power_carrier/power_carrier.kicad_sch)
3. **Auxiliary Board schematic:** [`pcbs/auxiliary-board/auxiliary-board.kicad_sch`](pcbs/auxiliary-board/auxiliary-board.kicad_sch)
4. **CAN HAT schematic (Waveshare):** [`docs/can/2-CH-CAN-HAT-Schematic.pdf`](docs/can/2-CH-CAN-HAT-Schematic.pdf)
5. **BOM:** [`docs/bom.ods`](docs/bom.ods)

<p>
  <img src="images/electro-pup-power-carrier-v1-render.png" width="48%" alt="Power Carrier">
  <img src="images/electro-pup-auxiliary-board-v1-render.png" width="48%" alt="Aux board">
</p>

PCBs: KiCad v8 · fabricated via JLCPCB. Extra libraries: [reubenstr/kicad-libraries](https://github.com/reubenstr/kicad-libraries).

---

## Software overview

<img src="images/electro-pup-block-diagram.png" width="800" alt="Block diagram">

- **UI:** React Native / Expo (web; Android without plot) — live vs sim overlays  
- **Kinematics / trajectories:** Bezier + arc projection — see `src/plot/`  
- **Simulation:** MuJoCo via `./src/sim.sh`  
- **Live robot:** `./src/main.sh` on Raspberry Pi OS Lite (Bookworm 64-bit)

Setup walkthrough: [`docs/setup.md`](docs/setup.md)

<img src="images/electro-pup-ui-live.png" width="800" alt="Live UI">

---

## Motors (MG4010E-i10v3)

- Voltage 7.4–32 V · CAN 1 Mbps · rated 2.5 N·m · max 4.5 N·m · 1:10 gear  
- Docs: [`docs/motors/`](docs/motors/)  
- Zero / verify: `src/zero.sh` / zero-motors script (see upstream notes)

CAN controller: [Waveshare 2-CH Isolated CAN HAT](https://www.waveshare.com/2-ch-can-hat.htm) (~70 Hz update per controller for 6 motors).

---

## CAD & 3D prints

Polymaker PolyMax Tough PLA recommended (see upstream print-time estimates).

**Local files:** [`cad/3D/v1/`](cad/3D/v1/) (STL + STEP)

**Onshape (upstream, export-enabled for non-commercial):**

- [Assembly](https://cad.onshape.com/documents/b02341d4ebb7f3e9dd488186)
- [Legs](https://cad.onshape.com/documents/6da583196278caf8e90b3122)
- [Body](https://cad.onshape.com/documents/280c24f1b6bdbe8246159786)
- [Hips](https://cad.onshape.com/documents/428031d0c98bf15dcc9f5c8c)
- [Tools](https://cad.onshape.com/documents/3677b35bffbfedb5a3fd2b26)
- [Parts](https://cad.onshape.com/documents/6d4d4e21394ee725ee8ddb38)
- [PCB](https://cad.onshape.com/documents/c8a855826c37bd92b89d9f0e)
- [Neopixels](https://cad.onshape.com/documents/567292ac55c75b2efa25b7d5)

---

## Getting started (high level)

1. Read [`docs/setup.md`](docs/setup.md) fully before buying parts.  
2. Order / print from [`docs/bom.ods`](docs/bom.ods) + [`docs/3d-prints.ods`](docs/3d-prints.ods).  
3. Fabricate PCBs from KiCad projects under [`pcbs/`](pcbs/).  
4. Flash aux firmware under [`firmware/aux/`](firmware/aux/) (PlatformIO).  
5. Clone this repo on the Pi and follow setup for Python venv + CAN.

```bash
git clone https://github.com/ajju2004srivatsan-cloud/ElectroPup.git
cd ElectroPup
```

Prefer upstream for issues when possible: [reubenstr/ElectroPup/issues](https://github.com/reubenstr/ElectroPup/issues).

---

## Credits (from upstream)

- IK / leg plotting ideas: [mike4192](https://github.com/mike4192/)  
- Carbon-tube frame inspiration: James Bruton / Open Dog 3  
- Related projects listed in [`docs/README_UPSTREAM.md`](docs/README_UPSTREAM.md)

**Primary design & implementation: [reubenstr](https://github.com/reubenstr).** This community fork only reorganizes documentation for easier discovery.

---

## AI / community note

Upstream discloses AI assistance for some coding/debugging. This fork’s documentation refinements were prepared to help the community find schematics and build files faster — not to rebrand the project.
