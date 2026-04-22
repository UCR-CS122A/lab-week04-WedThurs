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

## Pattern
You will build a network of Picos + FPGAs to control the light pattern on 12-LEDs.
The patterns should look as follows:

|  | Master Pico | Slave Pico | Slave FPGA |
|----------|----------|----------|----------|
| Pattern 1 |`0000`|`1111`|`0000`|
| Pattern 2 |`0001`|`1110`|`0001`|
| Pattern 3 |`0011`|`1100`|`0011`|
| Pattern 4 |`0111`|`1000`|`0111`|
| Pattern 5 |`1111`|`0000`|`1111`|

## System Description

You are creating a 3-device SPI network. This network houses two Picos, and one FPGA.

One of the picos will serve as the SPI master, the other two devices are SPI slaves.

The master pico generate a 12-bit pattern with each bit controlling one of the twelve LEDs.

4 LEDs are connected to the master Pico, another 4 to the slave pico, and the final 4 to the FPGA slave.

- 4 bits are used by the Master to control its 4 LEDs
- 4 bits are sent over SPI to the pico slave. The pico slave will consume the data, and update its value on the LEDs
- The last 4 bits are to be sent to the FPGA slave which will update its LEDs.

## [Demo Video]()
