# Step Mother 2 (RP2040) - PCB

Design files for the Step Mother 2 PCB: a 23-key USB MIDI step sequencer built around an
RP2040, with a USB-C socket, 20 LEDs driven by an IS31FL3731 and a 10 kOhm potentiometer.
Every component except the 23 keyswitches and the potentiometer is surface-mounted, so the
board can be assembled by machine, with no hand soldering of a controller module.

Files exported 12 November 2026 from EasyEDA Pro. The design check (DRC) passed with 0 issues
at export.

## What's in this folder

### 1_editable_design - open and modify the design

| File | Use it for |
|---|---|
| `StepMother2_EasyEDA-Pro_2026-11-12.epro2` | **EasyEDA Pro** (current format). Contains the schematic, PCB and the project's own part library. |
| `StepMother2_EasyEDA-Pro-V2_2026-11-12.epro` | The same project in the older EasyEDA Pro format. Use this one to import into **KiCad 8 or newer**, or into older EasyEDA Pro versions. |

- **EasyEDA Pro** (free, in the browser at pro.easyeda.com or as a desktop app): File > Open Project, or Import, and choose the `.epro2` file.
- **KiCad 8+**: File > Import > Non-KiCad Project > EasyEDA Pro, and choose the `.epro` file. Re-run KiCad's own design rule check after importing.

### 2_manufacturing - order bare or assembled boards

| File | What it is |
|---|---|
| `StepMother2_Gerber_2026-11-12.zip` | Gerbers and drill files. Upload the zip as-is; don't unzip it. |
| `StepMother2_BOM_2026-11-12.csv` | Bill of materials with LCSC part numbers, for JLCPCB/LCSC assembly. |
| `StepMother2_PickAndPlace_2026-11-12.csv` | Component positions and rotations (mm, top side). |

### 3_documentation - read without any EDA software

| File | What it is |
|---|---|
| `StepMother2_Schematic_2026-11-12.pdf` | Full schematic. |
| `StepMother2_PCB_Assembly_2026-11-12.pdf` | Placement and assembly drawings (top/bottom), BOM page and drill drawing. |
| `StepMother2_3D_2026-11-12.step` | 3D model of the assembled board, for designing or checking an enclosure (21 MB). **The RP2040 chip (U3) is missing from this model**: its 3D model could not be exported. It is low and does not affect enclosure fit. |

## Board specification

| | |
|---|---|
| Size | 150 x 110 mm |
| Layers | 2 |
| Thickness | **1.6 mm** (required: the keyswitches clip to a 1.6 mm board, and the enclosure is designed around it) |
| Material | FR-4 TG135 |
| Copper | 1 oz |
| Surface finish | ENIG recommended (the IS31FL3731 and the RP2040 have 0.4 mm pitch pads; avoid leaded HASL if you want RoHS compliance) |
| Components | top side only |

## Ordering from JLCPCB

The same steps as the Step Mother 1 (see [`../../v1-teensy/pcb/README.md`](../../v1-teensy/pcb/README.md)):
upload the Gerber zip (2 layers, 150 x 110 mm, **1.6 mm**, **ENIG**), then enable **Standard**
assembly on the **top side** with the BOM and pick-and-place files, and set **Confirm Parts
Placement: Yes** to approve JLCPCB's preview before production. Check the orientation of U1
(IS31FL3731), U3 (RP2040), the USB-C socket, the LEDs and the diodes against the silkscreen.

Unlike the Step Mother 1 there is no module to buy separately: every part in the BOM has an LCSC
number, so one assembly order covers the whole board. The 23 keyswitches (KEY1-KEY23) and the
potentiometer (R1) are through-hole parts; JLCPCB can assemble them, or you can untick them in
the parts-matching step and solder them yourself.

## Parts list (summary)

| Ref | Qty | Part | LCSC |
|---|---|---|---|
| U3 | 1 | RP2040, LQFN-56 | C2040 |
| U4 | 1 | W25Q16JVSSIQ flash, SOIC-8 | C131025 |
| X1 | 1 | 12 MHz crystal | C20625731 |
| U2 | 1 | AMS1117-3.3 regulator, SOT-223 | C6186 |
| USBC1 | 1 | USB-C receptacle TYPE-C-31-M-12 | C165948 |
| U1 | 1 | IS31FL3731-QFLS2-TR LED driver, QFN-28 | C191206 |
| D1-D23 | 23 | 1N4148W diode, SOD-123 | C5345962 |
| KEY1-KEY23 | 23 | CPG151101D06 keyswitch (MX-style) | C49234237 |
| LED1-LED20 | 20 | Red LED 0402 (YLED0402R) | C21260817 |
| R1 | 1 | 10 kOhm pot, ALPS RK09L1140A5P | C7419101 |

Capacitors and the remaining resistors are in the BOM CSV, which is the authoritative list.

## Firmware

The board runs the StepBro + Yummy Gummy firmware from the
[StepDaddy](https://github.com/AlexKokoschka/StepDaddy) repository. Its
[releases](https://github.com/AlexKokoschka/StepDaddy/releases) have StepDaddy, the updater,
and the `.uf2` file. A brand-new board opens an RPI-RP2 drive when plugged in; StepDaddy
installs the firmware on it.

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
