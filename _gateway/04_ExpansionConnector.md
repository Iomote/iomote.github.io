---
title: Expansion connector
position: 4
---

The expansion connector uses 3.3V level signals and is generally used for prototyping or to connect expansions, like the dev kit with sensors and display.

![Expansion Connector](./images/PinoutArduino.jpg){: class="img-doc-small"}

Expansion connector pinout:

| **PIN** | **NAME** | **DESCRIPTION** |
| :---: | :---: | --- |
| **1** | A0 | Analog input 0-3.3V (12bit ADC) |
| **2** | A1 | Analog input 0-3.3V (12bit ADC) |
| **3** | A2 | Analog input 0-3.3V (12bit ADC) |
| **4** | GND | Ground |
| **5** | D12 | Digital I/O |
| **6** | D6 | Digital I/O |
| **7** | D11 | Digital I/O |
| **8** | D5 | Digital I/O |
| **9** | D10 | SPI MISO signal |
| **10** | D4 | Front panel switch input (digital level: 1-open 0-pressed) |
| **11** | D9 | SPI MOSI signal |
| **12** | D3 | I2C Clock signal (*should be used as i2c only!*) |
| **13** | D8 | SPI Clock signal |
| **14** | D2 | I2C Data signal (*should be used as i2c only!*) |
| **15** | D7 | LED - Front panel led output (1-ON 0-OFF) |
| **16** | D1 | Serial1 RX (input) |
| **17** | RESET | Reset (*resets only Application processor!*) |
| **18** | D0 | Serial1 TX (output) |
| **19** | GND | Ground |
| **20** | 3V3 | Output (*limited to max 500mA*) |
