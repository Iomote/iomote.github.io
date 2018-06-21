---
title: Front panel
position: 3
---

### User Button (P1)
~~~ cpp
int Iomote.buttonRead( )
~~~
**Parameters**
- None

**Returns**
- **0** (or **LOW**) if button is pressed
- **HIGH** otherwise

---


### User LED (Status)
User LED can be driven using the default Arduino reference APIs. User LED is **pin 7**, its state can be changed using the standard Arduino functions `digitalWrite( ... )` or `analogWrite( ... )`
