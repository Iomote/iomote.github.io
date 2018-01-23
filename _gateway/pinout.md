---
title: Pinout
position: 2
---

Il dispositivo **X400** dispone di due connettori accessibili all'utente:
- **Connettore Industriale**: connettore a vite, suddiviso su due lati del dispositivo
- **Connettore Arduino-compatibile**: connettore con i segnali dell'**Application processor**

#### Connettore industriale
I seguenti segnali sono disposti su due connettori a vite, e disponibili nell'applicazione utente dell'**Application processor** tramite le librerie sviluppate da **Iomote** (per ulteriori informazioni vedere la sezione *Iomote library*).

![Architettura](./images/PinoutLayout.png){: class="img-doc"}

I segnali del connettore industriale sono:

| **PIN** | **NAME** | **DESCRIPTION** |
| :---: | :---: | --- |
| **1** | GND | Ground Input |
| **2** | VCC | Power supply input (9-24V 2A) |
| **3** | GND | Ground Input |
|**4** | DIG IN 1 | Digital input (Dry input) |
| **5** | DIG IN 2 | Digital input (Dry input) |
| **6** | RELAY NO | Relay normally open contact |
| **7** | RELAY C | Relay common contact |
| **8** | GND | Ground |
| **9** | DIG OUT | Digital output (open collector) |
| **10** | GND | Ground |
| **11** | AN 2 | Analog input 0-10V (12bit ADC) |
| **12** | AN 1 | Analog input 4-20mA (12bit ADC) |
| **13** | RS232-RTS | Serial port RS232 RTS (Output) |
| **14** | RS232-CTS | Serial port RS232 CTS (Input) |
| **15** | RS232-TX | Serial port RS232 TX (Output) |
| **16** | RS232-RX | Serial port RS232 RX (Input) |
| **17** | GND | Ground |
| **18** | RS485-B | Serial port RS485 (signal B) |
| **19** | RS485-A | Serial port RS485 (signal A) |

#### Connettore Arduino-Compatibile
I segnali dell'**Application processor** sono riportati su un connettore a 20 vie. I segnali sono connessi direttamente al microcontroller ARM Cortex-M0+ compatibile con Arduino.

**Nota**: tutti i segnali sono compatibili a livelli logici 0 - 3.3 V.

![Architettura](./images/PinoutArduino_01.jpg){: class="img-doc-small"}

| **PIN** | **NAME** | **DESCRIPTION** |
| :---: | :---: | --- |
| **1** | A0 | Analog input 0-3.3V (12bit ADC) |
| **2** | A1 | Analog input 0-3.3V (12bit ADC) |
| **3** | A2 | Analog input 0-3.3V (12bit ADC) |
| **4** | GND | Ground |
| **5** | 12 | Digital i/o |
| **6** | 6 | Digital i/o |
| **7** | 11 | Digital i/o |
| **8** | 5 | Digital i/o |
| **9** | 10 | SPI-MISO - SPI MISO signal |
| **10** | 4 | Front panel switch input (digital level: 1-open 0-pressed) |
| **11** | 9 | SPI-MOSI - SPI MOSI signal |
| **12** | 3 | I2C-SCL - I2C Clock signal (*should be used as i2c only!*) |
| **13** | 8 | SPI-SCK - SPI Clock signal |
| **14** | 2 | I2C-SDA - I2C Data signal (*should be used as i2c only!*) |
| **15** | 7 | LED - Front panel led output (1-ON 0-OFF) |
| **16** | 1 | UART-RX - Serial1 signal RX (input) |
| **17** | RESET | Reset (*resets only Application processor!*) |
| **18** | 0 | UART-TX - Serial1 signal TX (output) |
| **19** | GND | Ground |
| **20** | 3V3 | Output (*limited to max 500mA*) |

