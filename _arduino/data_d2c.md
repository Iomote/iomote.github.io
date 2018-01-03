---
title: Invio dei dati al Cloud
position: 3
description: Funzioni per inviare dati dall'applicazione utente al Cloud
---

### Formato dei dati
I messaggi del device Iomote X400 sono strutturati come stringhe contenenti un array di oggetti Json. Questo significa che ogni messaggio inviato al cloud può contenere 1 o più oggetti JSON, separati da una virgola (carattere). La dimensione massima (in byte) della stringa del messaggio formattato in questo modo non deve superare i 3750 byte.
Per ulteriori informazioni riguardo il formato dati JSON è possibile consultare il sito internet [JSON.org](https://www.json.org/).

Ogni oggetto JSON avrà un timestamp (generato automaticamente dall'**Iomote Core**), seguito da una serie di coppie chiave-valore forniti dall'applicazione eseguita dall'**Application Processor**.

Inizialmente il contenuto del messaggio è costituito da un solo oggetto JSON comprensivo di timestamp
~~~ json
[
  {
    "ts": 123456789
  }
]
~~~

In questo caso, l'applicazione utente non ha ancora inserito alcun dato e non ha annidato alcun oggetto JSON all'array.

Ora, l'applicazione utente potrà fornire per esempio una coppia chiave-valore all'**Iomote Core**, aggiungendo quindi dei dato all'oggetto JSON in lavorazione nel messaggio, tramite il comando `Iomote.append(...)`
~~~ json
[
  {
    "ts": 123456789,
    "chiave": "valore stringa"
  }
]
~~~
...e così procedendo, richiamando iterativamente il comando `Iomote.append(...)`
~~~ json
[
  {
    "ts": 123456789,
    "chiave": "valore stringa",
    "chiave2": "valore stringa 2"
  }
]
~~~
...
~~~ json
[
  {
    "ts": 123456789,
    "chiave": "valore stringa",
    "chiave2": "valore stringa 2",
    "chiave3": 1234,
    "chiave4": 54.09,
    "chiave5": false,
    "chiave6": "un nuovo valore stringa"
  }
]
~~~

L'applicazione utente potrà fornire coppie chiave-valore fino al raggiungimento del limite della dimensione del messaggio senza dover necessariamente creare un nuovo oggetto JSON all'interno del contenuto del messaggio.

Se invece avesse bisogno di creare un nuovo oggetto con un nuovo timestamp, potrà utilizzare il comando `Iomote.object()`. Il risultato sarà
~~~ json
[
  {
    "ts": 123456789,
    "chiave": "valore stringa",
    "chiave2": "valore stringa 2",
    "chiave3": 1234,
    "chiave4": 54.09,
    "chiave5": false,
    "chiave6": "un nuovo valore stringa"
  },
  {
    "ts": 123456794
  }
]
~~~
Da questo momento, se l'applicazione utente aggiungerà altre coppie chiave valore (tramite il metodo append), queste saranno inserite nel nuovo oggetto JSON:
~~~ json
[
  {
    "ts": 123456789,
    "chiave": "valore stringa",
    "chiave2": "valore stringa 2",
    "chiave3": 1234,
    "chiave4": 54.09,
    "chiave5": false,
    "chiave6": "un nuovo valore stringa"
  },
  {
    "ts": 123456794,
    "chiave_per_nuovo_oggetto": "valore del nuovo oggetto"
  }
]
~~~

In qualsiasi momento, il messaggio può essere inserito nella coda di invio dei messaggi verso il cloud tramite il comando `Iomote.send()`. In questo modo, tutto il contenuto del messaggio verrà inviato al Cloud quanto prima ed il contenuto del messaggio ritornerà quello iniziale con un solo oggetto JSON contenente il solo timestamp.
~~~ json
[
  {
    "ts": 123456796
  }
]
~~~

Il contenuto del messaggio in lavorazione è gestito nella memoria RAM (memoria volatile) dell'**Iomote Core** fino a che non viene iniziato l'invio dello stesso tramite il metodo `send()`. A questo punto, l'**Iomote Core** effettuerà dei tentativi di invio per vari minuti (in assenza di connettività internet il processo può fallire oppure essere molto lento). In ogni caso l'**Iomote Core** salverà il messaggio in questione in una memoria non volatile e tenterà di inviarlo nuovamente in un secondo tempo, dopo aver avuto conferma che la comunicazione con il Cloud sia funzionante.
Attualmente l'**Iomote Core** può memorizzare fino a 50 messaggi offline nella memoria non volatile.


*Nota:* Durante la creazione dei messaggi, se l'**Iomote Core** raggiunge il limite di dimensione prestabilito, non accetterà l'inserimento di nuovi dati nel messaggio fino a che non si utilizzerà il metodo `send()`. Ogni chiamata di *aggiunta chiave-valore* `append(...)` oppure *oggetto* `object()` restituirà nel codice utente un codice di errore. La lista dei codici di errore è disponibile nella sezione apposita.

E' possibile inviare anche dei messaggi di notifica alla dashboard Iomote. Tali messaggi hanno limite di lunghezza del testo di 100 bytes ma non devono rispettare il formato JSON dei messaggi descritto precedentemente.



### Funzioni disponibili
---
~~~ cpp
Iomote.append(key, value)
~~~
Permette la creazione di una coppia chiave-valore nell'oggetto JSON correntemente in lavorazione.
* Il primo parametro è il nome della chiave da aggiungere, in formato `char*`.
* Il secondo parametro può essere di tipologia variabile:
    * char* contentente il valore formato testuale da aggiungere
    * int o float con il valore numerico da aggiungere
    * bool con valore true oppure false

Risultato dell'operazione: 0 in caso di successo, altrimenti viene fornito un codice di errore.

*Nota* non è possibile creare più elementi con la stessa chiave in un oggetto JSON, non essendo previsto dallo standard JSON. Se si vuole usare una stessa chiave, è necessario creare un nuovo oggetto per ricevere tale chiave.

---
~~~ cpp
Iomote.object()
~~~
Permette di chiudere l'oggetto JSON correntemente in lavorazione e prepararne uno nuovo, popolato soltanto dal timestamp.

Risultato dell'operazione: 0 in caso di successo, altrimenti viene fornito un codice di errore.

---
~~~ cpp
Iomote.send()
~~~
Permette di finalizzare il messaggio JSON correntemente in lavorazione e di inserirlo nella coda di invio. Tale messaggio verrà automaticamente inviato non appena sarà possibile. Il messaggio viene inoltre salvato in una memoria non volatile, in modo da essere recuperato in caso di assenza di connettività oppure di alimentazione prolungata.

Risultato dell'operazione: 0 in caso di successo, altrimenti viene fornito un codice di errore.

---
~~~ cpp
Iomote.notification(int level, char* text)
~~~
Permette di inviare un messaggio di notifica alla dashboard del **MyMote Platform**.
* Il primo parametro è il livello di notifica
    * 0 = notification
    * 1 = warning
    * 2 = alarm
* Il second parametri è il messaggio testuale da inviare (fino a 100 bytes)

Risultato dell'operazione: 0 in caso di successo, altrimenti viene fornito un codice di errore.

