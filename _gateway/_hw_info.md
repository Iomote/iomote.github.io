---
title: Informazioni
position: 1
---

**X400** è un gateway programmabile e connesso dotato di diverse interfacce verso il mondo reale. **X400** è perfetto per connettere sensori (analogici, digitali) e macchinari (Seriali, ModBus o bus proprietari).

**X400** è facilmente adattabile a qualsiasi necessità grazie alla compatibilità con la IDE di Arduino con la quale è possibile creare facilmente applicazioni in pochi minuti. **X400** può essere utilizzato come sistema standalone o per applicazioni di Retrofit di macchinari e prodotti esistenti. 
Il gateway **X400** è gestibile da remoto tramite la semplice interfaccia Web che consente il Provisioning, l'aggiornamento remoto (OTA), ricevere allarmi/notifiche e tanto altro.
**X400** è Certificato per Microsoft Azure IoTHub che significa rispettare i massimi standard di sicurezza (TLS 1.2).

#### Hardware

Il dispositivo **X400** dispone di due processori che eseguono funzioni distinte:
* **Iomote Core Processor** E' il processore che gestisce autonomamente tutta la connettività con **Microsoft Azure IotHub** (inclusa la sicurezza tramite il **TLS 1.2**). Questo processore non necessita di programmazione. Oltre la gestione autonoma della connettività, l'**Iomote Core processor** gestise anche i messaggi dall'applicazione dell'utente, che viene eseguita dal processore **App processor** compatibile con l'ambiente Arduino.
* **App Processor** Un processore compatibile con **Arduino** a disposizione dell'utente per la creazione delle applicazioni: leggere sensori, gestire protocolli industriali 232, 485 o modbus, etc... il tutto a portata di mano, con un ambiente di sviluppo semplice ed immediato.

#### Interfacce
* 2 PORTE SERIALI (RS232/RS485)
* 2 DIGITAL IN (OPTO PROTECTED) 
* 1 DIGITAL OUT (OPEN COLLECTOR) 
* 1 RELE
* 1 ANALOG IN (0-10V)
* 1 ANALOG IN (4-20mA)
* ARDUINO PINS (I/O,UART,SPI,I2C)

#### Specifiche
* Certificato per Microsoft Azure
* Connettività: LAN o CELLULAR 3G
* SIM M2M e Dati inclusi
* Certificazione CE
* Alimentazione +9..+24V DC, 2A
* Temperatura -20..+80°C 
* Dimensioni 100*80*35mm
* Montabile su barra DIN


#### **Connettività**
Il dispositivo **X400** prevede una doppia connettività (Ethernet + 3G). Il dispositivo predilige automaticamente l'interfaccia ethernet per lo scambio dati con i servizi Cloud, ed utilizza la rete Mobile come soluzione di backup in caso si abbiano problemi con la rete LAN.

La scelta dell'interfaccia di rete viene effettuata **automaticamente** dal dispositivo tramite l'**Iomote Core processor**, a seconda delle condizioni riscontrate.


