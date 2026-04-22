# Lab Week 03 Mon-Tue

This lab, you'll be implementing Christmas light controller on the Pico. This time we aren't breaking it into exercises. We're just giving a high level description of the system.

You'll be exploring:
- Device-to-device communication
- Configuring SPI Communication on the RPPico
- Implementing SPI (slave) in Verilog

### Required components
1. FPGA (either ICESuger or ICESuger-pro)
1. 1x DIP switch (in total 1 switch will be used)
1. 2x Raspberry Pi Picos
1. 12x LEDs (with 220Ohm resistors)
1. Breadboard + enough wires to connect everything

### Wiring

- Connect four LEDs to each of the two picos, and the remaining four LEDs to the FPGA.
- Designate one of the two picos as the SPI Master, and hook up the slaves to the master.
  - This means allocating wires for CS, CLK, and MOSI (we don't need to worry about MISO, because the slaves don't reply)

## System Description

You are creating Christmas Lights! There will be two animated LED patterns that can be shown on 12 LEDs. You will control these LEDs across 3 devices--with each device controlling four LEDs.

The devices will speak with each other using the SPI communication protocol. The devices you have at hand: 2x picos, 1x FPGA.

One of the picos will serve as the SPI master, the other two devices as SPI slaves.

The master pico generates a 12-bit pattern with each bit controlling one of the twelve LEDs.
- 4 bits are used by the SPI Master to control its 4 LEDs
- 4 bits are sent over SPI to the pico slave. The pico slave will consume the data, and display the value on the LEDs
- The last 4 bits are to be sent to the FPGA slave which will update its LEDs.

A single switch toggles between two animations that can be displayed on the LEDs.

A potentiometer controls how fast the pattern proceeds through its animation. The potentiometer should increase (or decrease) the animation speed by 100ms.

## [Demo Video]()
