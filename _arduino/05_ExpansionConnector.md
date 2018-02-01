---
title: Expansion connector
position: 5
---

All the signals on Expansion connector can be used as any other Arduino signals. 
The only limitation is on I2C SDA and SCL signals, which should always be used as I2C Bus signals, since X400 **App processor** provides an onboard EEPROM. This non volatile memory can be used by **App processor** code, using any Arduino-compatible library. 

The EEPROM model is a 24AA64, it's address is A0.