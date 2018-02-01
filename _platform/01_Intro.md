---
title: Introduction
position: 1
---

**X400** is a programmable gateway that automatically connects to Microsoft Azure. It’s provided with **MyMote**: a web-based management dashboard for provisioning, device software update and other common IoT administration tasks.

X400 sends two different types of messages to the cloud: 
* **Data**: messages coming from the Arduino-App running on X400 such as sensors’ readings, machines status and many others.
Each message is forwarded to your queue on the Microsoft Azure Service Bus and it is available to any application (a web app, a function …). Each X400 gateway has a maximum of 100 messages per day (message size 3,75Kb)
* **Management**: messages exchanged with the cloud for admin operations (such as OTA device software update and others). **Notifications** are special messages coming from the device and visualized directly on MyMote web dashboard.


![Architettura](./images/Architettura.jpg){: class="img-doc"}
*MyMote platform architecture* 

MyMote can be accessed via browser on any device with username and password authentication. A set of **REST-API** are available to get information on each device or to automate device-level operations (OTA and others).
In the next chapters you will learn how to use MyMote platform and how to create App running on X400 gateway.
