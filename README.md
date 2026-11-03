# Step Mother

A handcrafted, open-source USB controller: 23 mechanical keys, 20 LEDs and a
knob, built around a Teensy 4.1. It shows up on a computer, iPhone or iPad as a
class-compliant USB audio and MIDI device, with no drivers needed.

It ships with firmware for music production, with two instruments in one:
**StepBro**, a MIDI step sequencer, and **Yummy Gummy**, a 303-style bass synth
with its own sequencer that streams 48 kHz audio over USB. Because the firmware
and the hardware are open, it can be reprogrammed into any kind of controller.

This repository holds the **hardware**: the PCB and the enclosure. The firmware,
the updater, the user manuals and the developer guide are in the
**[StepDaddy](https://github.com/AlexKokoschka/StepDaddy)** repository.

## Updating the firmware

Download **StepDaddy** for macOS or Windows from the
[StepDaddy releases](https://github.com/AlexKokoschka/StepDaddy/releases), open
it and follow the steps. The case stays closed and your patterns are kept.

## Documentation

- **User manuals** (PDF):
  [StepBro](https://github.com/AlexKokoschka/StepDaddy/blob/main/docs/manuals/StepBro_User_Manual_v1.0.0.pdf)
  and [Yummy Gummy](https://github.com/AlexKokoschka/StepDaddy/blob/main/docs/manuals/Yummy_User_Manual_v1.0.0.pdf)
- **[Developer guide](https://github.com/AlexKokoschka/StepDaddy/blob/main/docs/DEVELOPER_GUIDE.md)**:
  changing the firmware, writing your own, and the panel's wiring.

## Hardware revisions

| Folder | Board | Contents |
|---|---|---|
| [`v1-teensy/`](v1-teensy/) | Step Mother 1, Teensy 4.1 | [PCB](v1-teensy/pcb/README.md): EasyEDA Pro project (also imports into KiCad 8+), Gerbers, BOM and pick-and-place for JLCPCB, schematic and assembly PDFs, 3D model of the assembled board. [Enclosure](v1-teensy/enclosure/README.md): STL and STEP files to print, the FreeCAD source, and the mechanical interface for designing your own case. |

| | Step Mother 1 |
|---|---|
| Size | 16.5 × 12 × 2 cm, about 200 g |
| Processor | Teensy 4.1 (ARM Cortex-M7, 600 MHz) |
| Controls | 23 mechanical keys, 1 potentiometer, 20 LEDs (IS31FL3731) |
| USB | Micro-USB on the Teensy; class-compliant USB audio and MIDI |
| PCB | 150 × 110 mm, 2 layers, 1.6 mm |

## License

Copyright 2026 Alex Kokoschka.

The hardware in this repository (PCB and enclosure) is licensed under the
**CERN-OHL-S-2.0** (CERN Open Hardware Licence Version 2 - Strongly Reciprocal):
see `LICENSE`. You may use, modify, make and sell it; if you distribute a
modified design or products made from one, you must share its complete source
under the same licence.

The firmware and updater (StepDaddy repository) are licensed under GPL-3.0.

"TB-303" is a trademark of Roland Corporation; this project is not affiliated
with or endorsed by Roland.

SPDX-License-Identifier: CERN-OHL-S-2.0
