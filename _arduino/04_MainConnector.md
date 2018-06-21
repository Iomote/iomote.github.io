---
title: Main connector
position: 4
---

In this section will be covered all the commands to control the signals of the main connector. The commands are issued as methods of the object Iomote


---


### **Analog and digital IO**
~~~ cpp
float Iomote.analogRead(int channel)
~~~
**Parameters**
- **channel**: the analog channel you want to read. Main connector has two analog channels:
 - **AN_1** can be used to read channel 1, a 4-20mA input
 - **AN_2** can be used to read channel 2, a 0-10V.

**Returns**
- A float (floating point) number with the read value, in case of channel 1 the value is expressed in mA, in case of channel 2 is expressed in Volts


---


~~~ cpp
int Iomote.digitalRead(int input)
~~~
**Parameters**
- **input**: the digital input number you want to read. Main connector has two digital inputs, both can be used with 0 - 24V.
 - **DIG_IN1** can be used to read digital in 1
 - **DIG_IN2** can be used to read digital in 2
 - **BUTTON** can be used to read front panel button
**Returns**
A int number with the read value (LOW or HIGH)

---


~~~ cpp
void Iomote.digitalWrite(int pin, int value)
~~~
**Parameters**
- **input**: the digital output number you want to write. Main connector has two digital outputs:
 - **OC_OUT** is an open collector output
 - **RELAY_OUT** is the on-board relay
- **value**: the value you want to write (LOW or HIGH)

---

### **RS232/RS485 port**
Serial port of main connector can be used as RS232 or RS485, but not at the same time. All the methods of Arduino Serial class are wrapped to Iomote class methods with similar implementations.

~~~ cpp
void Iomote.serialBegin(int baudrate, uint8_t RS485_Mode)
~~~
**Parameters**
- **baudrate**: the Serial port baudrate to be used.
- **RS485_Mode**:
 - **RTS_CTS_OFF** can be used to set RS232 mode without RTC/CTS signals
 - **RTS_CTS_ON** can be used to set RS232 mode with RTC/CTS signals
 - **RS485** can be used to set RS485 mode

All the other Serial class methods can be used in the same way as Arduino Reference. Following is a table with all the available methods and their equivalent for RS232/RS485 port.

| **Arduino Reference** | | **Iomote class equivalent** |
| --- | --- | --- | 
| `Serial.end( )` | → | `Iomote.serialEnd( )` |
| `Serial.available( )` | → | `Iomote.serialAvailable( )` |
| `Serial.read( )` | → | `Iomote.serialRead( )` |
| `Serial.peek( )` | → | `Iomote.serialPeek( )` |
| `Serial.flush( )` | → | `Iomote.serialFlush( )` |
| `Serial.write( ... )` | → | `Iomote.serialWrite( ... )` |

