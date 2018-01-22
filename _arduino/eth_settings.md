---
title: Ethernet DHCP
position: 5
description: Settaggi avanzati per l'utilizzo dell'Ethernet in una rete priva di DHCP Server
---

I parametri DHCP di configurazione della rete ethernet possono essere configurati tramite una Applicazione eseguita dall'**Application Processor**.
Se il DHCP è disabilitato, tutti i parametri di rete devono essere correttamente impostati affinchè il dispositivo X400 comunichi correttamente con il Cloud utilizzando l'interfaccia di rete Ethernet.

### Settaggio dei parametri DHCP
I parametri DHCP forniti dall'applicazione sono memorizzati in una memoria "non volatile" e saranno quindi sempre utilizzati dall'**Iomote Core** ad ogni sua configurazione dell'interfaccia di rete etherent.
Se il dispositivo, quindi, ha precedentemente ricevuto una configurazione DHCP tramite una applicazione, tale configurazione sarà sempre utilizzata fino alla modifica da parte di una nuova applicazione con dati differenti.
Nel caso non sia più necessario usare dei parametri DHCP è bene ricordarsi di inserire i parametri default tramite una applicazione dell'**Application  Processor** per eliminare la vecchia configurazione.

---
~~~ cpp
Iomote.setDHCP(value)
~~~
Imposta l'utilizzo del DHCP Client. Se value è false, allora il DHCP Client è disabilitato e la connessione Ethernet utilizzerà i parametri forniti dall'utente.
---
~~~ cpp
Iomote.setIP(ip_0, ip_1, ip_2, ip_3)
~~~
Imposta l'IP del dispositivo nella rete ethernet (per esempio `Iomote.setIP(192,168,1,2);` forza l'utlizzo del valore 192.168.1.2 come IP statico)
---
~~~ cpp
Iomote.setSubnet(ip_0, ip_1, ip_2, ip_3)
~~~
Imposta l'IP del subnet mask
---
~~~ cpp
Iomote.setGateway(ip_0, ip_1, ip_2, ip_3)
~~~
Imposta l'IP del Gateway (generalmente l'indirizzo del router)
---
~~~ cpp
Iomote.setDNS(ip_0, ip_1, ip_2, ip_3)
~~~
Imposta l'IP da utilizzare per il server DNS 
---
~~~ cpp
Iomote.applyNetConfig()
~~~
Tale funzione invia tutta la configurazione precedentemente impostata all'**Iomote Core**. Da questo momento in poi la configurazione viene memorizzata e l'interfaccia ethernet utilizzerà tale configurazione per connettersi alla rete.

Risultato dell'operazione: 0 in caso di successo, altrimenti viene fornito un codice di errore.

### Come rispristinare l'utilizzo del client DHCP
Per ripristinare l'utilizzo del DHCP è sufficiente impostare il parametro con i comandi
~~~ cpp
Iomote.setDHCP(true);
Iomote.applyNetConfig();
~~~
