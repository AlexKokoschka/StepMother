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

The four screw posts have a plain Ø4.7 mm x 4.3 mm blind hole with a 0.3 mm lead-in chamfer,
for a brass insert. Do not ask your print service to tap them.

## Parts you need besides the case

| Part | Qty | Notes |
|---|---|---|
| Brass threaded insert, M3 x 0.5, 4.0 mm long, 4.6 mm outer diameter (knurled, slightly tapered) | 4 | Ruthex M3 short, RX-M3S x 4.0 (Galaxus item 42703715, bag of 100). Galaxus lists the outer diameter as 3 mm, but that is the thread size; the real outer diameter is 4.6 mm. |
| M3 x 12 mm countersunk screw, hex socket (DIN 7991 / ISO 10642), A2 stainless | 4 | Epower M3 x 12 (Galaxus item 8599195, pack of 10). 12 mm includes the head; 2 mm hex key. |
| Two-part epoxy | | To fix the inserts in the posts (see Assembly). |
| XDA profile 1U keycap, MX | 23 | 16 transparent, 7 can be solid (see below) |
| Knob for 6 mm D-shaft | 1 | |

The inserts are sold as heat-set inserts, but in a resin shell they are **epoxied in** rather
than melted in. The posts leave only 4.3 mm of depth between the hole and the top face, which is
why the short (4.0 mm) insert is used; a standard M3 insert is about 6 mm. The screws are
designed to be driven once the epoxy has cured, and the case is designed to be closed once.

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
3. Epoxy the four brass inserts into the posts (narrow end first, flush with the bottom of
   the post), and let the epoxy cure before going on. Keep epoxy out of the thread.
4. Seat the bottom plate into the rebate. It recesses 0.3 mm so it cannot rock.
5. Drive the four screws from underneath into the inserts. The bottom plate has Ø3.4 mm
   clearance holes with a Ø6.5 mm, 90 degree countersink; a screw head sits about 0.25 mm below
   the plate surface. Each screw engages about 2.2-2.4 mm of insert thread and leaves about
   1.8 mm of free hole above its tip.
6. Press on the keycaps and the knob.

## Known tight dimensions

These are fine but have little margin. If you modify anything, re-check them.

- **Keycap clearance 1.00 mm.** The top face's outer surface sits 5.00 mm above the PCB and a
  fitted keycap bottoms out at 6.00 mm. This is the binding constraint of the whole design.
- **Screw length.** About 1.8 mm of free hole remains above the screw tip. Do not use a longer
  screw than 12 mm.
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
