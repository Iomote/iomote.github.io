---
title: Using Microsoft Visual Studio Code
position: 10
description: How to use Microsoft Visual Studio code to develop X400 App processor apps
--- 


[**Microsoft Visual Studio Code**](https://code.visualstudio.com) is a lightweight but powerful source code editor which runs on your desktop and is available for Windows, macOS and Linux. Its functionalities can be increased using marketplace extensions.

For our development purposes, using Microsoft's *Arduino for Visual Studio Code* extension, it is possible to write and compile Arduino-compatible code.

### Preparation of Visual Studio Code
First of all, install Visual Studio Code from the [**product page**](https://code.visualstudio.com/).

> **Warning:**
> 
> To use the *Arduino for Visual studio code* extension, it is mandatory to install the Arduino IDE on your system. Please refer to the [**Getting Started**](/#gettingstarted01_BeforeStarting) section.
{: .warning}

Once **Arduino IDE** is corretly installed on your computer, open **Visual Studio Code** and install the *Arduino for Visual Studio Code* extension:
* Open the menu *View -> Extensions*
* On the search bar type **vscode-arduino** and select it
* Install the extension and restart Visual Studio Code


### Configure an **Iomote X400 App processor** project
To create an **App processor** project you have to open a folder usign the menu **File -> Open Folder...** (create a blank folder if needed).

Open the command panel usign **F1 key** and type *Arduino: Initialize* command. It will be prompted you to choose a name to proceede, use the name you prefer. For the board model, choose **Iomote X400**.

A blank project is ready.

Now it's time to import the **iomoteClass** library to your project.
* Press **F1 key**
* On command panel type **Arduino: Library Manager**
* Serach for **iomoteClass** library and **include** it on the project.

The **Iomote X400 App processor** code can now be written using **Visual Studio Code**. For further reference on vscode-arduino extension you can refer to it's [**official page**](https://github.com/Microsoft/vscode-arduino) or on [**extension marketplace page**](https://marketplace.visualstudio.com/items?itemName=vsciot-vscode.vscode-arduino).


