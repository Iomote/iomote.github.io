---
title: Preparazione del dispositivo (associazione account utente)
position: 2
description: Prima accensione del dispositivo
---

Un dispositivo X400 non ancora associato ad alcun account si connette automaticamente all'IoT hub di gestione. Non serve scrivere alcune codice, la connessione viene effettuata automaticamente tramite il cavo ethernet: l'unico vincolo è di poter disporre di un router/access point connesso ad internet con DHCP Server abilitato (generalmente tutti i router sono configurati in tal modo).
Un dispositivo ancora non associato ad alcun account utente può essere considerato come dispositivo "orfano". Le informazioni necessarie per poter effettuare il passaggio all'IoT hub dell'account utente vengono fornite tramite l'IotHub di gestione. Una volta che il dispositivo viene associato all'account utente, l'X400 modificherà automaticamente le sue impostazioni e si sposterà sul nuovo IoT hub. Da questo momento, l'utente potrà scambiare i dati con il dispositivo, ricevere i messaggi, etc...

Per associare il dispositivo al proprio account è necessario inserire la stringa *device key* compilando il form di configurazione del dispositivo della piattaforma **MyMote Platform**, associandolo così al proprio account. La stringa **device key** può essere ricevuta tramite le librerie per Arduino (vedere la sezione dedicata).

Da questo momento in poi, il dispositivo invierà i dati dell'applicazione al service bus dedicato all'utente.
