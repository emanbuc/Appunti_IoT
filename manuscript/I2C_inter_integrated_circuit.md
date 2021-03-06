# I2C

source:

https://en.wikipedia.org/wiki/I%C2%B2C

http://www.byteparadigm.com/applications/introduction-to-i2c-and-spi-protocols/

The I²C bus was developed in 1982; its original purpose was to provide an easy way to connect a CPU to peripherals chips in a TV set. Peripheral devices in embedded systems are often connected to the microcontroller as memory-mapped I/O devices. One common way to do this is connecting the peripherals to the microcontroller parallel address and data busses. This results in lots of wiring on the PCB (printed circuit board) and additional ‘glue logic’ to decode the address bus on which all the peripherals are connected. In order to spare microcontroller pins, additional logic and make the PCBs simpler – in order words, to lower the costs – Philips labs in Eindhoven (The Netherlands) invented the ‘Inter-Integrated Circuit’, IIC or I²C protocol that only requires 2 wires for connecting all the peripheral to a microcontroller. The original specification defined a bus speed of 100 kbps (kilo bits per second). The specification was reviewed several times, notably introducing the 400 kbps speed in 1995 and – since 1998, 3.4 Mbps for even faster peripherals.
