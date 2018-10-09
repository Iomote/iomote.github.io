---
title: Initialization
position: 2
---


### Iomote object initialization
Most of the following commands leverages on the object Iomote, that is instantiated during the initialization phase. In the setup function it must be initialized using the proper command:
~~~ cpp
void Iomote.begin(const char *appname, uint8_t vers0, uint8_t vers1, uint8_t vers2)
~~~
**Parameters**
- **appname**: the buffer containing the name of the app (max length 100 chars).
- **vers0, vers1, vers2**: main, middle and lower version number for the app. (values: 0-255 for each number)

**Returns**
- None

The method initializes the hardware and communicates the Application name and version to the **Iomote Core** processor. Those parameters are sent to the Cloud only when changed, keep in mind each device has a max number of messages available per day.

> **NOTE**: in order to avoid confusion we suggest to keep the same name for your Apps on MyMote dashboard
{: .warning}

> **WARNING**: the **Iomote.begin** method is mandatory for the app to work properly. NEVER remove it from your code!
{: .error}

The **App name and App version** running on a specific device are shown on *MyMote - Devices section*.


---


### Reading the Device Key
~~~ cpp
int8_t Iomote.devKey(char* buffer)
~~~
**Parameters**
- **buffer**: the char buffer where the device key will be stored.

**Returns**
- 0 in case of success
- error code (refer to error codes table)
 
With this method it’s possible to read the **Device Key**. The key is long 64 chars and it’s returned as terminated array char, so the buffer must be **at least 65 chars**.


---


### Syncing the real time clock
~~~ cpp
time_t Iomote.rtcSync()
~~~
**Parameters**
- None

**Returns**
- a time_t variable containing the updated date/time. 
 
The internal RTC of the application processor is update at the device startup, but sometimes it may happens (especially with no internet connection) that the date/time is not updated so, at runtime, it's possible to force an update with this command. 

