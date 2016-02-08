## Pin configuration

| Pin | Function | Direction | Device | Device pin | Comments |
|----:|:---------|:----------|:-------|------------|----------|
|   0 | RX0      | In        | MCP2200 or XRF | TX | |
|   1 | TX0      | Out       | MCP2200 or XRF | RX | | 
|   2 | RX1      | In        | NVC08  | TX         | |
|   3 | TX1      | Out       | NVC08  | RX         | |
|   4 |          | Out  | Ethernet shield microSD | /CS | Reserved, not used |
|   5 |          | Out       | XRF    | /Reset     | |
|   6 | INT2     | In        | NVC08  | /PPS | Previously AS3935 interrupt |
|   7 |          | Out       | XRF    | Sleep      | |
|   8 |          | Out       | Fan    | Enable     | |
|   9 |          | Out       | MAX619 | Shutdown   | |
|  10 | /SS      | Out       | W5100/W5500 | /CS   | |
|  11 | MOSI     | Out       | SPI bus |         | W5100/W5500, microSD etc |
|  12 | MISO     | In        | SPI bus |         | W5100/W5500, microSD etc |
|  13 | SCK      | Out       | SPI bus |         | W5100/W5500, microSD etc |
|  14 |          | -         | -      |            | Previously AS3935 SDA |
|  15 | TOSC1    | In        | RTC    | SQW        | For software RTC |
|  16 | (JTAG TDI) | In/out  | MLX90614 | SDA      | SoftWire I2C |
|  17 | (JTAG TDO) | -       | -      |            | Previously AS3935 SCL |
|  18 | (JTAG TMS) | Out     | MLX90614/heater | Power/enable | |
|  19 | (JTAG TCK) | In/out  | MLX90614 | SCL      | SoftWire I2C |
|  20 | SDA      | In/out    | RTC, MCP3424 | SDA  | Hardware I2C |
|  21 | SCL      | In/out    | RTC, MCP3424 | SCL  | Hardware I2C |
|  22 |          | (Out)     | Calunium microSD | /CS | Reserved, not used |
|  23 |          | In        | XRF    | ON         |  |
|  A0 |          | Out       | NVC08  | /Reset     |  |
|  A1 |          | -         | -      |            |          |
|  A2 |          | In        | Vin    |            | Vin voltage measurement |
|  A3 |          | -         | -      |            |          |
|  A4 |          | In/out    | HIH61xx | SDA       | SoftWire I2C |
|  A5 |          | In/out    | HIH61xx | SCL       | SoftWire I2C |
|  A6 |          | Out       | LM61   | power      |          |
|  A7 |          | In        | LM61   | output     |          |

Direction is given with respect to the microcontroller.
