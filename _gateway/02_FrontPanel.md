---
title: Front panel
position: 2
---

The front panel of the X400 contains:
- **Button "RESET"**: resets only the app-processor (not the Iomote Core) and restarts the app.
- **Button "P1"**: button available for the user application
- **LED "CLOUD"**: shows the status of the cloud connection
- **LED "STATUS"**: Led available for the user application
- **micro USB port**: serial port to communicate with the app-processor, can be used to download the app on the device and for debug purposes.

![X400 Front Panel](./images/X400_FrontPanel.png){: class="img-doc"}
*X400 Front Panel*

The front leds show the status of the device in several conditions reported in the table:

| **CLOUD** | **STATUS** | **DESCRIPTION** |
| --- | --- | --- |
| - | GREEN fast blink | App-processor restarting |
| RED fixed | - | Hardware fault (device will be reset in 1 min) |
| RED blinking | - | Network - Error |
| ORANGE blinking | - | Network - Connecting |
| ORANGE fixed | - | Network - Disconnected (device automatically will try to reconnect in few seconds) |
| GREEN blinking | - | Cloud - Connecting |
| GREEN fixed | - | Cloud - Connected |
| GREEN/ORANGE blinking | - | FOTA OS/App |

