---
title: Device provisioning
position: 2
---

> **IMPORTANT**:
>
> For the first installation of a new X400 device (even for cellular versions) you need an Internet connection via ethernet (with a DHCP enabled router).
{: .warning}

At startup X400 connects automatically to the cloud, waiting to be paired with a specific account.

Login using your username and password on [**cloud.iomote.com**](https://cloud.iomote.com) and go to **Devices** page and click on "**ADD +**" button. You will be required to insert name and **Device Key** of your gateway, location and group are optional. *Since it is probably your first device, Groups may not be available yet on your account. Don't worry: you can create groups and assign devices to any created groups later.*

> **How to get the Device Key?**
> 
> The factory app pre-loaded on X400, writes on the USB-serial port the Device Key. To read it: 
> - connect the front USB to your computer 
> - use a serial monitor tool (Arduino IDE has its one), with the settings 115200 8/N/1.
> - push the front button P1 and the device will write the Device Key on the serial port, copy and paste it on the MyMote portal
> 
> If you have overwritten the default app and you need the device key, don’t worry, you can find the code of the app in the [**Iomote GitHub account**](https://github.com/Iomote/iomote-app-devkey) or just use the proper command in you app to read the Device Key (have a look a the [**initialization section**](https://docs.google.com/document/d/1yJOB3ct0TSuOxcGN5tL5LuFSMi37jdozUVO83th4qzE/edit#heading=h.wez3w4c8veml))
{: .success}

When the form is filled, the device is reset. The operation will be confirmed by the front **CLOUD LED** colors (you can refer [**here**](https://docs.google.com/document/d/1yJOB3ct0TSuOxcGN5tL5LuFSMi37jdozUVO83th4qzE/edit#heading=h.osskawmgsfjm)). Just wait for the LED to become firmly **GREEN**.

Once the pairing procedure is complete, your device communicates with your MyMote cloud (it takes up to five minutes to see your device online, even if it’s already up and running, and you can already send data to the cloud). In the meantime the SIM card of the device is activated (if your device has 2G/3G features), the activation process may take up to two hours.

