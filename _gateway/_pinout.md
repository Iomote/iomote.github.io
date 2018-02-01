---
title: Pinout
position: 2
---

Il dispositivo **X400** dispone di due connettori accessibili all'utente:
- **Connettore Industriale**: connettore a vite, suddiviso su due lati del dispositivo
- **Connettore di espansione**: connettore con i segnali dell'**Application processor**

### Connettore industriale
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

### Connettore di espansione
I segnali dell'**Application processor** sono riportati su un connettore a 2x10 vie di espansione. I segnali sono connessi direttamente al microcontroller ARM Cortex-M0+ compatibile con Arduino.

**Nota**: tutti i segnali sono compatibili a livelli logici 0 - 3.3 V.

![Architettura](./images/PinoutArduino_01.jpg){: class="img-doc-small"}

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

