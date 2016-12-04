# Using SPI with ESP8266


source: http://d.av.id.au/blog/esp8266-hardware-spi-hspi-general-info-and-pinout/

The ESP8266 datasheet reports that there are two hardware SPI ports named SPI and HSPI by Espressif.

**SPI**: This SPI port is capable of quad data channels and has 3x chip select pins available. However, it is already in use on 99.9% of modules where the operational code is loaded off a flash rom chip. In theory can be used also for user operation, but it's very difficult. Usage of SPI port is not supported by ArduinoCore libraries.


**HSPI**: Presumably this is meant to stand for HardwareSPI. This is the SPI available to the user for external device conneciton. The pinout is below.

| Pin Name | GPIO# | HSPI Function |
| -- | -- | -- |
|MTDI |GPIO12 |MISO (DIN)|
|MTCK |GPIO13 |MOSI (DOUT)|
|MTMS |GPIO14|CLOCK|
|MTDO |GPIO15|CS / SS |

Pin Name in the table are the one given in the datasheet. These names are pretty confusing! 
* MTCK is NOT the clock for the HSPI, but the DataOut line.
* MTDO (data out) pin. it's actually the HSPI Chip Select line

*Note: some ESP module don't break out all required PIN. In order to use HSPI posrt you must use a module like ESP-12 with all pins exposed.*

In ArduinoCore libraries the SPI pin are defined accoridng to the table below and hooked to the HSPI port in https://github.com/esp8266/Arduino/blob/master/variants/generic/common.h 

``` 
#define PIN_SPI_SS   (15)
#define PIN_SPI_MOSI (13)
#define PIN_SPI_MISO (12)
#define PIN_SPI_SCK  (14)
```
SPI library use the pin definition above, but allow the  a different GPIO to be passed during initializzation phase (see SD card code).

## GPIO15 Wiring
TBC

GPIO15 needs to be tied to GND when booting from the onboard SPI flash (see ESP8266 boot mode). In order to use this pin as chip select you can not connect directly to the groud, but you must use a pull down resistor.
(see ESP8266 schematics).





