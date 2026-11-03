# Step Mother 1 (Teensy 4.1) - Enclosure

A two-part 3D-printed case for the Step Mother 1 PCB: a shell with a raised
turret over the Teensy 4.1 (its USB socket is the case's USB opening) and a
bottom plate.

## What's in this folder

| Folder | File | Use it for |
|---|---|---|
| `print/` | `StepMother1_Teensy_Shell.stl`, `StepMother1_Teensy_BottomPlate.stl` | Printing. |
| `print/` | `StepMother1_Teensy_Shell.step`, `StepMother1_Teensy_BottomPlate.step` | The same parts as STEP, for CAD or for print services that prefer it. |
| `source/` | `StepMother1_Teensy_Enclosure.FCStd` | The editable design ([FreeCAD](https://www.freecad.org/)). |
| `design-your-own/` | `MECHANICAL_INTERFACE.md` | Everything you need to design your own case: board outline, mounting holes, switch and pot positions, the Teensy keepout and the USB opening. |
| `design-your-own/` | `StepMother1_Teensy_FitCheck.step` | A simplified board model (switches, keycaps at full press, pot, Teensy keepout) to check a design against. |

## Printing

The switch openings are sized 16.80 mm against the switches' 16.00 mm collar
(+0.40 mm per side), which suits powder-bed processes (about ±0.3 mm). Read
`design-your-own/MECHANICAL_INTERFACE.md` before changing any opening or the
top face: the top face must stay below 6.00 mm above the PCB, or the keys
bottom out before they actuate.

The case fits a 1.6 mm PCB and a Teensy 4.1 soldered so that its top sits
4.0 mm above the PCB (see `../pcb/README.md`).

## Licence

Copyright 2026 Alex Kokoschka

Licensed under the **CERN-OHL-S v2** (CERN Open Hardware Licence Version 2 -
Strongly Reciprocal), like the PCB. The full text is in
`LICENSE` at the top of this repository.

SPDX-License-Identifier: CERN-OHL-S-2.0

Source location: https://github.com/AlexKokoschka/StepMother
