---
title: Using third party libraries
position: 9
--- 


### Suggestion on hardware initialization
To allow the correct initialization of **X400 App processor** peripherals and the communication with **Iomote Core processor**, we highly suggest you to place the `Iomote.begin(...)` function as first command of Arduino `setup()` method.
All the further third party initialization functions can be placed after that command.

As reference example, you can refer to [**Iomote Starter Kit Example code**](https://github.com/Iomote/iomote-app-starterkit).

---

### Debug Monitor
#### Serial object definition
Many Arduino examples use the `Serial` object as main debug interface. To use the very same naming convention with 
**Iomote X400** (or any other Arduino Cortex-M0+ based board) you can define the **Serial** name on code:
~~~ cpp
#define Serial SerialUSB // use Serial1 for external connector pins UART or SerialUSB for CDC USB Uart
~~~

User can define **Serial** as **SerialUSB** if it plans to use the micro USB CDC port, or **Serial1** to use the UART port on expansion connector.

---

#### Waiting for PC connection on microUSB port

If **App processor** uses the SerialUSB port as debug interface, you can use the following code snippet to allow the application to wait for some seconds before to send data on serial port.

~~~ cpp
SerialUSB.begin(115200);
int maxSerialWaiting = 2000; // up to 2 seconds...
while((!SerialUSB) && (maxSerialWaiting > 0))
{
	maxSerialWaiting--;
	delay(1);
}
~~~

Such code snippet can be places inside the `setup()` function.
