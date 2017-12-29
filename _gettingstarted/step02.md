---
title: Preparazione del dispositivo (associazione account utente)
position: 2
---

Una volta alimentato il dispositivo X400 si connette automaticamente all'IoT hub di gestione. Non serve scrivere alcune codice, la connessione viene effettuata automaticamente tramite il cavo ethernet: l'unico vincolo è di poter disporre di un router/access point connesso ad internet con DHCP Server abilitato (generalmente tutti i router sono configurati in tal modo).
Un dispositivo ancora non associato ad alcun account utente può essere considerato come dispositivo "orfano", e quindi si connette all'IoT hub di gestione per poter ricevere le dovute informazioni necessarie a poter effettuare il passaggio all'IoT hub dell'account utente. Una volta che il dispositivo viene associato all'account utente, l'X400 modificherà automaticamente le sue impostazioni e si sposterà sul nuovo IoT hub. Da questo momento, l'utente potrà scambiare i dati con il dispositivo, ricevere i messaggi, etc...

Per associare il dispositivo al proprio account è necessario eseguire la scansione del QR code in dotazione. Seguendo il link riportato nella URL del QR code, l'utente dovrà compilare il form di configurazione del dispositivo della piattaforma **MyMote Platform**, associandolo così al proprio account.