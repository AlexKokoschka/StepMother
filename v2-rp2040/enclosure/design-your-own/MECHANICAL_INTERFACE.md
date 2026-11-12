# Step Mother v2 (RP2040) — Mechanical Interface

What you need to design your own enclosure for this board.

## Coordinate system

All figures in millimetres. Origin at the PCB's lower-left corner.
**Z = 0 is the PCB underside; Z = 1.60 is the PCB top surface.**
Heights below are quoted **above the PCB top surface** unless stated otherwise.

In the supplied enclosure STEP files the board sits at **+4.50, +4.50, +8.50** relative to this
frame. Add that offset to compare your design against the supplied case.

## Board

| | |
|---|---|
| Outline | 150.00 x 110.00 |
| Thickness | 1.60 |
| Mounting holes | 4 x diameter 3.20, through |
| Hole positions | (8, 8) · (8, 102) · (146, 8) · **(146, 90)** |

Note the fourth hole is at **y = 90**, not 102. The pattern is not symmetric.

## Switch grid

Pitch 19.05. Grid points at X and Y = 20.00 / 39.05 / 58.10 / 77.15 / 96.20.
Of the 25 positions, **23 are populated**: the potentiometer occupies (96.20, 77.15) and the
position at (96.20, 96.20) is deliberately left empty to give the knob room.

**True mechanical switch centres** = grid + (0.63, -3.81):

* X = 20.63 / 39.68 / 58.73 / 77.78 / 96.83
* Y = 16.19 / 35.24 / 54.29 / 73.34 / 92.39

### Do not use the pick-and-place coordinates

The P&P file reports the **footprint origin**, which EasyEDA places at the centroid of the pads.
That has no fixed relationship to the part's mechanical features.

* **Switches:** a Cherry MX footprint puts its pins at (-3.81, 2.54) and (2.54, 5.08) relative
  to the stem. Their midpoint is (-0.635, +3.81) — hence the +0.63, -3.81 offset.
* **Pot:** its pins sit at y 73.40 and its mounting lugs at y 80.90. Midpoint 77.15, which is
  exactly what the P&P reports, while the shaft axis is at 80.90 — a 3.75 mm error.

Derive mechanical positions from the drill/copper geometry or the 3D model, and cross-check
the two against each other.

## THE KEYCAP CONSTRAINT — read this first

**Any part of your enclosure's top face must stay below 6.00 mm above the PCB top surface.**

A fitted keycap bottoms out with its skirt at exactly that height. A face any higher stops the
key before it reaches its actuation point, and the switch never registers — the keyboard feels
like it works and does nothing. The supplied design puts its outer top surface at 5.00 mm,
leaving 1.00 mm.

An early revision of this case had the face at 8.70 mm. It would have been unusable.

## Switch profile (Cherry MX compatible, heights above PCB top)

| Feature | Size | From | To |
|---|---|---|---|
| Lower body | 14.00 sq | 0.00 | 5.25 |
| **Collar (widest point)** | **15.60 x 16.00** | **5.50** | **6.00** |
| Upper body, tapering | 14.87 -> 11.98 | 6.25 | 11.50 |
| Stem | 4.00 sq | 12.50 | 15.10 |

The switches are soldered before the case goes on, so your top face must pass **down over** an
assembled switch. The opening has to clear the 15.60 x 16.00 collar, not just the stem.

## Potentiometer (ALPS RK09L1140A5P)

| | |
|---|---|
| Shaft axis | **(96.20, 80.90)** |
| Body envelope, 0.4 to 8.6 above PCB | X 90.85..101.55 · Y 73.30..85.75 |
| Bushing | diameter 9.00, from 10.00 to about 15.00 |
| Shaft | diameter 6.00 with a D-flat, to about 25.00 |

The body is asymmetric about the shaft: 7.60 below and 4.85 above the axis in Y, because the
terminal block projects toward -Y. No circle centred on the shaft can contain it and still clear
the neighbouring switch opening — it would need roughly 22 mm diameter.

## Tolerance

3D-printed parts of this size are typically quoted at about ±0.3% with a **±0.3 mm lower limit**,
so features smaller than that sit inside the process noise. The supplied design sizes the switch openings at 16.80 against
a 16.00 collar — **+0.40 mm per side** — for exactly this reason. Do not design to +0.20.

## Using FitCheck.step

A simplified board model, drawn from primitives, in the coordinate frame above. 97 solids:

* 1 PCB slab with the four mounting holes
* 23 x 4 per switch — collar envelope (0 to 6.0), upper body (6.0 to 11.5), stem (11.5 to 15.1),
  and **the keycap at full press** (6.0 to 15.5, 18.40 square)
* 3 for the pot — body envelope, bushing, shaft
* 1 for the **USB-C receptacle** — X 117.32..126.26, Y 101.67..109.57, Z 0.75..4.85 (board frame)

**If your design intersects the keycap solids, the keys will not actuate.** That is the single
most useful thing this file does.

## USB-C

| | |
|---|---|
| Receptacle | X 117.32..126.26 · Y 101.67..109.57 |
| Height | **3.25 above the PCB top** (Z 0.75..4.85 in the board frame) |
| Edge | +Y, stopping 0.43 mm short of the board edge |

The supplied case opens X 115.29..128.29 and Z -1.20..+3.80 relative to the PCB top, giving
1.95 mm each side, 0.32 below and 0.47 above.

**This is the only component that will not fit under a flat 2.5 mm top face.** Its top is
3.25 mm above the board and the underside of a 2.5-above-PCB face sits at 2.50. The supplied
shell solves it with a local pocket in the face underside, leaving 1.20 mm of material there.

## Tallest components

| Part | Height above PCB |
|---|---|
| Keyswitch stem | 15.10 |
| Pot shaft | about 25 |
| **USB-C receptacle** | **3.25** |
| U4 (SOIC-8) | 2.07 |
| Everything else | 1.75 or less |

Apart from the switches, the pot and the USB connector, nothing on this board is taller than
2.1 mm.
