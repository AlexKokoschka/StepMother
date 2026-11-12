# Step Mother 2 (RP2040) - Enclosure

A two-part 3D-printed case for the Step Mother 2 PCB, made for **SLA (resin) printing**: a
one-piece outer shell (top face and all four walls, no visible side seam) with a flat top, and a
flat bottom plate that recesses up into it. Every fastener is on the underside. Overall size
159 x 119 x 23.1 mm.

**This case is for the Step Mother 2 only.** Its USB-C opening is in a different place from the
Step Mother 1's micro-USB opening, so the two cases are not interchangeable. Look at the socket
on your board: USB-C means this case, micro-USB means [`../../v1-teensy/enclosure/`](../../v1-teensy/enclosure/).

## What's in this folder

| Folder | File | Use it for |
|---|---|---|
| `print/` | `StepMother2_RP2040_Shell.stl`, `StepMother2_RP2040_BottomPlate.stl` | Printing. If you only want a case printed, these are the only files you need. |
| `print/` | `StepMother2_RP2040_Shell.step`, `StepMother2_RP2040_BottomPlate.step` | The same two parts as exact surfaces, for CAD or for print services that prefer STEP. |
| `source/` | `StepMother2_RP2040_Enclosure.FCStd` | The editable design ([FreeCAD](https://www.freecad.org/)), containing only the two solids. |
| `design-your-own/` | `MECHANICAL_INTERFACE.md` | Everything you need to design your own case: board outline, mounting holes, switch and pot positions, the USB-C opening and the height limits. |
| `design-your-own/` | `StepMother2_RP2040_FitCheck.step` | A simplified board model (switches, keycaps at full press, pot, USB-C) to check a design against. Built from primitives. |

## Printing

Print on an SLA (resin) printer. The shell is a deep open box with 23 through-openings, and the
engraved text on the top face has strokes down to 1.0 mm, which is why the case is not designed
for FDM: with a 0.4 mm nozzle the engraving does not come out cleanly, and printed open-side-down
the whole 2.5 mm top face becomes a ceiling over a large void that fills with support.

The switch openings are sized 16.80 mm against the switches' 16.00 mm collar (+0.40 mm per
side). Read `design-your-own/MECHANICAL_INTERFACE.md` before changing any opening or the top face:
the top face must stay below 6.00 mm above the PCB, or the keys bottom out before they actuate.

Ask for **no threads** if your print service offers tapping: the four screw posts are pilot
holes that the screws thread themselves.

## Parts you need besides the case

| Part | Qty | Notes |
|---|---|---|
| M3 x 14 mm countersunk self-tapping screw | 4 | Wheelspin Models MV22053 or equivalent |
| XDA profile 1U keycap, MX | 23 | 16 transparent, 7 can be solid (see below) |
| Knob for 6 mm D-shaft | 1 | |

Do not use heat-set inserts: there is only 4.3 mm of depth between the post and the top face,
and a standard M3 insert wants about 6 mm. The case is designed to be closed once.

### Which keycaps need to be transparent

There are no LED apertures in the top face: the LEDs light the keys **through** the caps.

- **The 16 caps on the 4 x 4 step grid should be transparent.** They show step position and
  pattern state, and an opaque cap there means no lighting at all.
- **The 7 function caps can be solid.** The LED glow reflecting off the surrounding top shell is
  enough to tell their state.

## Assembly

1. Lower the shell straight down over the populated board. It clears every component on a
   vertical path, so no tilting is needed.
2. Fit the pot's M9 nut from above, through the knob island.
3. Seat the bottom plate into the rebate. It recesses 0.3 mm so it cannot rock.
4. Drive the four screws from underneath. They form their own thread in the shell's posts.
5. Press on the keycaps and the knob.

## Known tight dimensions

These are fine but have little margin. If you modify anything, re-check them.

- **Keycap clearance 1.00 mm.** The top face's outer surface sits 5.00 mm above the PCB and a
  fitted keycap bottoms out at 6.00 mm. This is the binding constraint of the whole design.
- **Screw tip to pilot bottom: 0.09 mm.** The pilot depth has no margin to give up.
- **Switch opening clearance: 0.40 mm** on the narrow axis.
- **USB-C: 0.47 mm** above the connector, 0.32 mm below.

## Changes from the Step Mother 1 case

Teensy turret removed (flat top); USB opening moved and resized for the on-board USB-C, with a
local relief pocket over the connector; bottom lip 1.0 to 1.2 mm with a correspondingly smaller
plate; the katakana moved to the top face, engraved, 8.7 mm, with the diacritics drawn as
geometry so every stroke is at least 1.0 mm.

## Licence

Copyright 2026 Alex Kokoschka

Licensed under the **CERN-OHL-S v2** (CERN Open Hardware Licence Version 2 - Strongly
Reciprocal), like the PCB. The full text is in `LICENSE` at the top of this repository. If you
modify the design and distribute it, or a product made from it, you must publish your modified
design files under the same licence.

A completely different enclosure designed from `MECHANICAL_INTERFACE.md` is an independent work
using published facts about a board, not a derivative of this design. The firmware is a separate
work with its own licence.

Add this to the header of any design file you modify:

```
Copyright (C) 2026 <your name>
Licensed under CERN-OHL-S v2 or any later version.
Source location: https://github.com/AlexKokoschka/StepMother
```

SPDX-License-Identifier: CERN-OHL-S-2.0

Source location: https://github.com/AlexKokoschka/StepMother
