---
title: Intro
position: 1
---

X400 is composed by two parts:
- **Iomote Core**: running Iomote OS, manages the communication with the cloud (Ethernet, celllular…), the security and the off-line messages storage. It solely serves as “cloud postman” for the App-processor.
- **App-processor**: Arduino-compatible, available to run your specific application such as a reading a sensor or interfacing a serial device. It is directly wired with the connectors of the gateway. 


These two parts communicate with easy-to-use serial API, so the App-processor can easily send data to the cloud, without. 

![X400 System Architecture](./images/X400_SystemArchitecture.png){: class="img-doc"}
*X400 System Architecture*


X400 offers several connectors with I/O, serial port and other signals managed by the App-processor.

- **Front panel**: status leds and pushbuttons
- **Main connector**: screw connectors on both sides of X400
- **Expansion connector**: TTL level signals  (3.3V)