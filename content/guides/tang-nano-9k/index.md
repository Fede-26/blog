---
title: "Guide to use the Tang Nano 9k FPGA board"
date: 2024-02-09
categories: "Guides"
tags:
    - FPGA
draft: false
langs: "English"
---

# Package

- GW1NR-9C
- QFN88P
- C6/I5
- LV

# Pinout

- Clock *(27MHz)*: `52`
- Leds:
  - Pins: `10`-`16` (w/o `12`)
  - Commone anode *(inverted signal)*
  - 1.8V Bank3
- Buttons:
  - Pins: `3`-`4`
  - Pull-up resistors *(inverted signal)*
  - 1.8V Bank3

# Gowin EDA (Linux)

## Installation

To execute `bin/gw_eda` rename `lib/librfreetype.so` to something else.

Next you need to install or compile [openFPGALoader](https://trabucayre.github.io/openFPGALoader/guide/install.html) to load the bitstream to SRAM or Flash.

## License

For the license you can use the education edition of the Gowin EDA, or apply for a free license on the gowin website.
In alternative you can use the public license server of sipeed:

- IP: `43.128.7.128`
- Port: `10559`

Be aware that some public wifi networks block access to these ports.

## Use

Just launch `./bin/gw_eda` from the terminal.
