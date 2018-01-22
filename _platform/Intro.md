---
title: Introduzione
position: 1
---

**X400** è un gateway nativamente connesso all’**IoT Hub di Microsoft Azure**, gestito dalla **MyMote platform** di Iomote per quanto riguarda il provisioning, l’aggiornamento del framework di comunicazione e della app utente. La comunicazione del device avviene esclusivamente con l’IoT Hub della MyMote platform, ma all’interno di esso avviene un routing del tipo di messaggio. Sono previste due tipologie:
* **Data**: sono i messaggi inviati dalla app utente che gira sul device, possono contenere letture di uno o più sensori, o altri valori direttamente letti sul campo, vengono formattati automaticamente all'interno di un JSON e vengono instradati direttamente su un service bus specifico per l'utente, in modo che possa leggere e utilizzare quei dati direttamente nella sua applicazione cloud, che potrà strutturare secondo le sue esigenze. 
* **Management**: sono quei messaggi che servono a eseguire le varie operazioni di gestione e manutenzione dei device come app e firmware update over the air (**OTA**), metriche di invio del traffico, notifiche. Le notifiche vengono inviate tramite comandi appositi dalla app, ma vengono instradati sulla MyMote platform.

![Architettura](./images/Architettura.jpg){: class="img-doc"}
*Architettura della piattaforma e della comunicazione con i device* 

L'utente avrà modo di accedere alla MyMote platform tramite browser, autenticandosi con username e password, oppure, tramite **API**, dalla propria applicazione, per ottenere informazioni sui device o eseguire operazioni su di essi in maniera programmatica. 
Nei seguenti paragrafi verranno analizzate le varie sezioni della MyMote platform e le relative funzionalità.
