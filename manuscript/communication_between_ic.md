# Comunicazioni tra circuiti integrati

TBC

## Comunicazione Sincrona ed Asincrona

TBC

### Comunicazione asincrona su porta seriale UART
Source: https://learn.sparkfun.com/tutorials/serial-peripheral-interface-spi 

A common serial port, the kind with TX and RX lines, is called “asynchronous” (not synchronous) because there is no control over when data is sent or any guarantee that both sides are running at precisely the same rate. Since computers normally rely on everything being synchronized to a single “clock” (the main crystal attached to a computer that drives everything), this can be a problem when two systems with slightly different clocks try to communicate with each other.

To work around this problem, asynchronous serial connections add extra start and stop bits to each byte help the receiver sync up to data as it arrives. Both sides must also agree on the transmission speed (such as 9600 bits per second) in advance. Slight differences in the transmission rate aren’t a problem because the receiver re-syncs at the start of each byte.


![alt text](images/async_serial_communication.png "Comunicazione asincrona")

(By the way, if you noticed that “11001010” does not equal 0x53 in the above diagram, kudos to your attention to detail. Serial protocols will often send the least significant bits first, so the smallest bit is on the far left. The lower nybble is actually 0011 = 0x3, and the upper nybble is 0101 = 0x5.)

Asynchronous serial works just fine, but has a lot of overhead in both the extra start and stop bits sent with every byte, and the complex hardware required to send and receive data. And as you’ve probably noticed in your own projects, if both sides aren’t set to the same speed, the received data will be garbage. This is because the receiver is sampling the bits at very specific times (the arrows in the above diagram). If the receiver is looking at the wrong times, it will see the wrong bits.

### Comunicazione Sincrona SPI

SPI works in a slightly different manner. It’s a “synchronous” data bus, which means that it uses separate lines for data and a “clock” that keeps both sides in perfect sync. The clock is an oscillating signal that tells the receiver exactly when to sample the bits on the data line. This could be the rising (low to high) or falling (high to low) edge of the clock signal; the datasheet will specify which one to use. When the receiver detects that edge, it will immediately look at the data line to read the next bit (see the arrows in the below diagram). Because the clock is sent along with the data, specifying the speed isn’t important, although devices will have a top speed at which they can operate (We’ll discuss choosing the proper clock edge and speed in a bit).

![alt text](images/sync_spi_communication.png "Comunicazione asincrona")

One reason that SPI is so popular is that the receiving hardware can be a simple shift register. This is a much simpler (and cheaper!) piece of hardware than the full-up UART (Universal Asynchronous Receiver / Transmitter) that asynchronous serial requires.

## Common Communication Port and Protocols

Below a list of communication port and protocol commonly used in microcontroller and embedded system

 * [UART](UART_universal_asynchronous_receiver_transmitter.md)
 * [I2C](I2C_inter_integrated_circuit.md)
 * [SPI](SPI_serial_parall_interface.md)

 * [PDM](PDM_pulse_density_modulation.md)
 * [I2S](I2S_inter_ic_sound.md)