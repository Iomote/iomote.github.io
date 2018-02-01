---
title: Provisioning
description: Add a new Device to your account
position: 3
---

Click on **ADD + button** to start the provisioning of a new device.
On the form you are asked to insert:
* **Device Key**: it’s the unique ID of the device (64 chars).
* **Name**: Friendly name.
* **Location**: Manual entry the gps position (Lat,Lon)
* **Group**: assign the device to a specific group


![Add Device](./images/DevicesPage_AddDevice.png){: class="img-doc"}*Adding a new device*

Things to keep in mind before adding a new device:
* **Internet connection**: for the first installation the device must be connected via Lan Cable (even for the 2G/3G versions) to a DHCP enabled router.
* **Computer and USB cable**: to read the **device key** connect the device to a PC via USB. Open a serial monitor software (115.200 baud/8/N/1) and at after the boot the device will write its device key.
* **SIM activation**: X400 models provided with 2G/3G connectivity are provided with a SIM card. Please note that the activation of the SIM may take up to 2 hours (only the first time).
