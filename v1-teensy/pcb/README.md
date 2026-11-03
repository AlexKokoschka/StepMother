# Step Mother 1 (Teensy 4.1) - PCB

Design files for the Step Mother 1 PCB: a 23-key USB MIDI step sequencer built around a
Teensy 4.1, with 20 LEDs driven by an IS31FL3731 and a 50 kOhm potentiometer.

Files exported 1 November 2026 from EasyEDA Pro. The design check (DRC) passed with 0 issues at export.

## What's in this folder

### 1_editable_design - open and modify the design

| File | Use it for |
|---|---|
| `StepMother1_EasyEDA-Pro_2026-11-01.epro2` | **EasyEDA Pro** (current format). Contains the schematic, PCB and the project's own part library. |
| `StepMother1_EasyEDA-Pro-V2_2026-11-01.epro` | The same project in the older EasyEDA Pro format. Use this one to import into **KiCad 8 or newer**, or into older EasyEDA Pro versions. |

- **EasyEDA Pro** (free, in the browser at pro.easyeda.com or as a desktop app): File > Open Project, or Import, and choose the `.epro2` file.
- **KiCad 8+**: File > Import > Non-KiCad Project > EasyEDA Pro, and choose the `.epro` file. Re-run KiCad's own design rule check after importing.

### 2_manufacturing - order bare or assembled boards

| File | What it is |
|---|---|
| `StepMother1_Gerber_2026-11-01.zip` | Gerbers and drill files. Upload the zip as-is; don't unzip it. |
| `StepMother1_BOM_2026-11-01.csv` | Bill of materials with LCSC part numbers, for JLCPCB/LCSC assembly. |
| `StepMother1_PickAndPlace_2026-11-01.csv` | Component positions and rotations (mm, top side). |

### 3_documentation - read without any EDA software

| File | What it is |
|---|---|
| `StepMother1_Schematic_2026-11-01.pdf` | Full schematic. |
| `StepMother1_PCB_Assembly_2026-11-01.pdf` | Placement and assembly drawings (top/bottom), BOM page and drill drawing. |
| `StepMother1_3D_2026-11-01.step` | 3D model of the assembled board, for designing or checking an enclosure (30 MB, so not kept in this folder: download it from the [StepDaddy 1.0.0 release](https://github.com/AlexKokoschka/StepDaddy/releases/tag/v1.0.0)). |

## Board specification

| | |
|---|---|
| Size | 150 x 110 mm |
| Layers | 2 |
| Thickness | **1.6 mm** (required: the keyswitches clip to a 1.6 mm board, and the Step Mother enclosure is designed around it) |
| Material | FR-4 TG135 |
| Copper | 1 oz |
| Surface finish | ENIG recommended (the IS31FL3731 has 0.4 mm pitch pads; avoid leaded HASL if you want RoHS compliance) |
| Smallest via | 0.3 mm hole / 0.6 mm pad |
| Components | top side only |

## Ordering from JLCPCB (tested)

### 1. PCB

1. Upload the Gerber zip.
2. Keep the detected 2 layers and 150 x 110 mm.
3. Set **thickness 1.6 mm** and **surface finish ENIG**.
4. Optional:
   - "Mark on PCB: Remove Mark" keeps JLCPCB's order number off the board.
   - "Confirm Production File: Yes" lets you approve the final files before production.

### 2. PCB Assembly

1. Switch assembly on: **Standard**, **top side**.
2. Upload the BOM and pick-and-place files.
3. Set **Confirm Parts Placement: Yes**.
   - JLCPCB then sends a preview to approve.
   - Check the orientation of U1 (IS31FL3731), the LEDs and the diodes against the silkscreen.
4. Edge rails: let JLCPCB add them, and choose their **depaneling** service so the board edges stay clean for the enclosure.

### 3. Parts JLCPCB cannot supply

**H1, the Teensy 4.1** (PJRC), has no LCSC number.

- Leave H1 unselected in the parts-matching step.
- Buy the Teensy from PJRC or a distributor.
- Solder it by hand.
- On the reference build, the Teensy's top surface sits 4.0 mm above the PCB, and its USB connector top is about 7 mm above the PCB. The enclosure's Teensy cut-out is sized for that height.

### 4. Through-hole parts

The 23 keyswitches (KEY1-KEY23) and the potentiometer (R1) are through-hole parts.

- JLCPCB can assemble them for you.
- Or untick them in the parts-matching step and solder them yourself.

## Parts list (summary)

| Ref | Qty | Part | LCSC |
|---|---|---|---|
| D1-D23 | 23 | 1N4148W diode, SOD-123 | C5345962 |
| KEY1-KEY23 | 23 | CPG151101D06 keyswitch (MX-style) | C49234237 |
| LED1-LED20 | 20 | Red LED 0402 (YLED0402R) | C21260817 |
| R1 | 1 | 50 kOhm pot, ALPS RK09L1140A5P | C231764 |
| R2 | 1 | 20 kOhm 0603 (IS31FL3731 R-EXT) | C4184 |
| U1 | 1 | IS31FL3731-QFLS2-TR LED driver, QFN-28 | C191206 |
| H1 | 1 | Teensy 4.1 (PJRC) | - (buy separately) |

The BOM CSV is the authoritative list.

## Firmware

The board runs the StepBro + Yummy Gummy firmware from the
[StepDaddy](https://github.com/AlexKokoschka/StepDaddy) repository. Its
[releases](https://github.com/AlexKokoschka/StepDaddy/releases) have StepDaddy, the
updater, and the `.hex` file.

## Enclosure

See [`../enclosure/`](../enclosure/).

## Licence

Copyright 2026 Alex Kokoschka

This source describes Open Hardware and is licensed under the **CERN-OHL-S v2**
(CERN Open Hardware Licence Version 2 - Strongly Reciprocal). The full text is in
`LICENSE` at the top of this repository, and is also published at https://ohwr.org/cern_ohl_s_v2.txt

SPDX-License-Identifier: CERN-OHL-S-2.0

You may redistribute and modify this source and make products using it under the terms of
the CERN-OHL-S v2. This source is distributed WITHOUT ANY EXPRESS OR IMPLIED WARRANTY,
INCLUDING OF MERCHANTABILITY, SATISFACTORY QUALITY AND FITNESS FOR A PARTICULAR PURPOSE.
Please see the CERN-OHL-S v2 for applicable conditions.

Source location: https://github.com/AlexKokoschka/StepMother

As the licence requires, anyone who distributes this design, or products made from it, must
provide the complete source of any modified version under the same licence, and must tell
recipients where that source can be found.
