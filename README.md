## Introduction
<p> This hat allows for connecting external devices to Chainbus with UART, I2C and SPI protocol


## Description
### Provided protcols

| Bus   | Voltage            | Selcection pin   | Header | Pinout                        |
| ----- | ------------------ | ---------------- | ------ | ----------------------------- |
| I2C   | 3V3                | Always connected | J4     | GND, 3V3, SDA 3V3, SCL 3V3    |
| I2C   | 5V                 | Always connected | J6     | GND, 5V, SDA 5V, SCL 5V       |
| ---   | ---                | ---------------- | ------ | --------------------------    |
| UART1 | Selectable on J8   | Default ON, P00  | J11    | GND, VCC, RX, TX              |
| UART2 | Selectable on  J14 | Default OFF, P06 | J15    | GND, VCC, RX, TX              |
| ---   | ---                | ---------------- | ------ | --------------------------    |
| SPI   | Selectable on J5   | Default ON, P13  | J7     | GND, VCC, SCK, MOSI, MISO, CS |

### Selecting bus lines
<p> Bus lines are conected through tri-state buffers with voltage level converters (with exception of I2C buses which are always connected) to chainbus header (through the standard bus swich of course).
<p> To select between UART1 and UART2 you need to set "selection" pin of the bus as output, and set logic level. 1 -> connected, 0 -> not connected. They are driven by TCA9535PWR with all addres pins (A0, A1, A2) connected to GND
<p> "Selected" Led's only work when manually enabling the buses. If you use "Default ON" functionality they might not be lighting up.
<p> By default, the Output Enable pins are connected through 10k resistor to either GND or VCC

### Bonus pins
<p> In order to achieve compability with non-standard sensord some addtional pins have been provided on the board. They are uniderctional and are connected to same tri-state buffers as some of buses. Bus belonging to a pin must be switched ON in order for them to work. Bonus pins will have same voltage as the bus it belongs to

| Tri-state buffer bus | Header | Pinout             | Input pins    | Output pins   |
| -------------------- | ------ | ------------------ | ------------- | ------------- |
| UART1                | J12    | P01, P02, P03, P04 | P01           | P02, P03, P04 |
| UART2                | J13    | P07, P10, P11, P12 | P07           | P10, P11, P12 |
| SPi                  | J9     | P14, P15, P16, P17 | P14, P15, P16 | P17           |