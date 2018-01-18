---
title: Inizializzazione
position: 2
description: Inizializzazione dell'hardware e dell'applicazione
---

### Iomote.begin
~~~ cpp
Iomote.begin(const char *appname, uint8_t vers0, uint8_t vers1, uint8_t vers2)
~~~

La funzione begin permette di inizializzare tutte le periferiche custom
* Il LED utente viene inizializzato come uscita digitale
* Il pulsante utente (accessibile tramite il frontale del dispositivo) è inpostato come ingresso (resistenza di pulled up interna)
* Le uscite digitali e gli ingressi analogici e digitali del connettore a vite sono inizializzati opportunamente
* Il segnale che comande il relay è impostato come uscita
* Le interfacce RS232 / RS485 non vengono inizializzate in quanto sono stati previsti comandi distinti per queste periferiche

La funzione `begin` comunica anche il nome dell'applicazione e la sua versione all'**Iomote Core**. Quest'ultimo analizza i dati ricevuti, e se trova modifiche con la versione precedente invia il nuovo dato al Cloud. In questo modo si può tenere traccia dell'applicazione attualmente in funzione nell' **Application Processor**. 
Il nome della versione (parametro appname) deve essere inferiore a 20 bytes. La versione può essere specificata tramite tre bytes (numeri da 0 a 255).
*Nota:* il mantenimento di nome e versione di app sono a discrezione dell'utente. La piattaform **MyMote Platform** non esegue alcuna verifica sul contenuto reale dell'applicazione, nè può tanto meno "capire" quale applicazione è effettivamente in esecuzione se l'utente non modifica di sua iniziativa tali parametri.
A titolo di esempio, chiamando la funzione Iomote.begin("my app", 1,2,3); verrà impostato il nome "my app" con versione 1.2.3.

La funzione begin sincronizza anche l'RTC dell'**Application Processor** con il valore UTC attuale: **Iomote Core** prende il valore del timestamp UTC da server online, in modo da avere calendario ed orario sincronizzati con valori reali. La libreria delegata alla gestione dell'RTC è la RTCZero (una libreria ufficiale arduino), per ogni ulteriore informazione si prega di far riferimento alla documentazione di tale libreria.

### Iomote.devKeyRead
~~~ cpp
Iomote.devKeyRead(char* devKeyBuff)
~~~

La funzione devKeyRead permette di copiare la stringa devKey nel buffer devKeyBuff fornito dall'utente.
* **Nota**: il buffer devKeyBuff deve essere un array di char di almeno 65 bytes.
* La stringa **devKey** serve ad effettuare l'associazione del dispositivo con l'account utente nel portale della **MyMote Platform**.

Risultato dell'operazione: 0 in caso di successo, altrimenti viene fornito un codice di errore.

### Debug: Interfacce Seriali Disponibili
Per poter avere *messaggi di debug su un monitor seriale* (per esempio il Serial Monitor dell'IDE Arduino), e quindi tenere traccia dell'esecuzione dell'applicazione utente, due interfacce seriali sono disponibili: **Serial1** e **SerialUSB**. 
* **Serial1** è una interfaccia UART situata sul connettore di espansione del dispositivo X400. Per poter utilizzare questa interfaccia con un PC è necessario collegare un convertitore USB-UART con livelli logici a 3.3V.
* **SerialUSB** invece è una interfaccia CDC che viene creata dall'**Application Processor** durante l'esecuzione dell'applicazione. E' dunque possibile utilizzare tale interfaccia seriale semplicemente collegando il cavo USB ad un PC/MAC. 

    * *Nota:* l'interfaccia SerialUSB viene scollegata durante l'aggiornamento dell'applicazione, quindi bisogna tenere in considerazione che ad ogni riavvio dell'applicazione è necessario eseguire una nuova connessione alla porta CDC tramite il monitor seriale.

Queste due interfacce seriali si comportano compatibilmente a quanto descritto nella documentazione ufficiale Arduino [Arduino Language Reference](https://www.arduino.cc/reference/en/). Pertanto rimandiamo alla documentazione ufficiale per ulteriori informazioni a tal proposito.
