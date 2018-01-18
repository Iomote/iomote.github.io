---
title: Invio dei dati al Cloud
position: 3
description: Funzioni per inviare dati dall'applicazione utente al Cloud
---

### Tipologia dei messaggi
Ci sono due tipi di dati che possono essere inviati tramite il device X400:
* messaggi
* notifiche

I messaggi hanno lunghezza massima di 3750 byte. In caso si superi tale lunghezza, le librerie restituiranno un errore (la lista dei codici di errore è disponibile nella sezione dedicata).
Ogni dispositivo può inviare un numero predefinito di messaggi giornalieri. Tale conteggio viene ripristinato ogni mezzanotte (orario UTC).
Il messaggio può essere inoltrato all'**Iomote Core** tramite la funzione `Iomote.message(...)`. A questo punto, l'**Iomote Core** effettuerà dei tentativi di invio per vari minuti (in assenza di connettività internet il processo può fallire oppure essere molto lento). In ogni caso l'**Iomote Core** salverà il messaggio in questione in una memoria non volatile e tenterà di inviarlo nuovamente in un secondo tempo, dopo aver avuto conferma che la comunicazione con il Cloud sia funzionante.
Attualmente l'**Iomote Core** può memorizzare fino a 50 messaggi offline nella memoria non volatile.


E' possibile inviare anche dei messaggi di notifica alla dashboard Iomote. Tali messaggi hanno limite di lunghezza del testo di 100 bytes. Tali messaggi possono essere inviati tramite la funzione `Iomote.notification(...)`.



### Funzioni disponibili
---
~~~ cpp
Iomote.message(char* payload)
~~~
Permette di inserire il messaggio **payload** fornito nella coda dei messaggi dell'**Iomote Core**. Tale messaggio verrà automaticamente inviato non appena sarà possibile. Il messaggio viene inoltre salvato in una memoria non volatile, in modo da essere recuperato in caso di assenza di connettività oppure di alimentazione prolungata.

Risultato dell'operazione: 0 in caso di successo, altrimenti viene fornito un codice di errore.

---
~~~ cpp
Iomote.notification(int level, char* payload)
~~~
Permette di inviare un messaggio di notifica alla dashboard del **MyMote Platform**.
* Il primo parametro (**level**) è il livello di notifica
    * 0 = notification
    * 1 = warning
    * 2 = alarm
* Il secondo parametro (**payload**) è il messaggio testuale da inviare (fino a 100 bytes)

Risultato dell'operazione: 0 in caso di successo, altrimenti viene fornito un codice di errore.

