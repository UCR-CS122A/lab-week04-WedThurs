# Lab Week 03 Mon-Tue

This lab, you'll be implementing Christmas light controller on the Pico

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

## Exercise 1
Program one Raspberry Pi Pico so that it displays distinct christmas-light patterns on 4x LEDs.

## Exercise 2
Configure the last Pico so that it serves as the SPI Master. Add another Pico so that it serves as the SPI slave.
The master PICO should generate an 8-bit long pattern. 4 of the bits should be displayed on the LEDs controlled by the master.
The other 4-bits should be sent to the slave pico over SPI. The slave pico should then display the pattern recieved from the mater on its 4 LEDs.

## Exercise 3
Implement a Verilog SPI Module configured to operate in slave mode.

The FPGA, like the other slave, will recieve a 4 bit payload from the master Pico which it will then display on its own LEDs.
