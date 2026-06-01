A single-board computer built around a W65C02S 6502 CPU. It uses a Lattice ICE40HX4K FPGA as a custom chipset. The FPGA handles video, audio, keyboard, storage, and address decoding.

---

## Hardware

| Part | What it does |
|------|-------------|
| W65C02S | Main CPU, socketed |
| ICE40HX4K | FPGA chipset for video, audio, IO |
| 62256 SRAM | 32K RAM, socketed |
| AT28C256 EEPROM | 32K ROM, socketed |
| SN74LVC8T245 × 2 | 5V ↔ 3.3V level shifters for the data bus |
| FT230XS | USB-to-UART bridge for debug |
| MicroSD slot | SPI storage via FPGA |
| VGA connector | 640×480 @ 60Hz, resistor ladder DAC |
| PS/2 connector | Keyboard input, decoded in FPGA |


---

## Memory map

```
0x0000 – 0x7FFF   RAM
0x8000 – 0x8FFF   FPGA registers / VRAM window
0x9000 – 0xBFFF   Expansion
0xC000 – 0xFFFF   ROM
```

---

## Schematic sheets

```
V-6502.kicad_sch       root
├── Power.kicad_sch    USB-C, TVS, LDOs, decoupling
├── CPU.kicad_sch      W65C02S, clock, reset
├── Memory.kicad_sch   SRAM, EEPROM
├── LevelShift.kicad_sch   SN74LVC8T245 data bus bridges
├── FPGA.kicad_sch     ICE40HX4K, config flash, oscillator
├── VGA.kicad_sch      DE-15, RGB resistor ladder
├── PS2.kicad_sch      Mini-DIN-6, ESD, pull-ups
├── SD.kicad_sch       MicroSD slot, SPI
├── Audio.kicad_sch    Buzzer, 3.5mm jack
└── Debug.kicad_sch    FT230XS, UART header, test points
```

---

## Status

**Schematic done.** ERC passes clean.

**PCB layout in progress.** The power section is partially routed. 

