---
title: Gestione device
position: 2
---

Nella pagina **Device** è possibile collegare nuovi dispositivi all'account utente e monitorare quelli attualmente presenti. Ogni device è caratterizzato dalle seguenti proprietà:

- **Nome**: il nome che gli è stato assegnato al momento dell'associazione con l'account utente.
- **Tipo**: il tipo di device, ad esempio X400.
- **Firmware version**: la versione del firmware di comunicazione verso Azure dell' **Iomote Core**.
- **App name & version**: la app e la relativa versione installata dall'utente sull' **Application Processor**.
- **Localizzazione**: coordinate geografiche del device, assegnate dall'utente.

![Devices](./images/devices.jpg){: class="img-doc"}*Pagina di gestione dei device*

Nella sezione centrale è presente l'elenco di tutti i device con le proprietà di base, incluso lo stato della connessione. Cliccando è possibile visualizzare tutti i dettagli, inclusi il numero di messaggi inviati durante la settimana.

La pagina è divisa in due parti:
- **Sezione centrale**: è visualizzato l'elenco di tutti i device accoppiati con l'account e le relative informazioni di base, incluso lo stato della connessione. 
- **Sezione dettagli**: viene attivata per ogni singolo device cliccando sulla tabella della sezione centrale. Contiene le informazioni dettagliate relative a ogni singolo device e la possibilità di aggiornare i firmware di comunicazione o le app. 


## Associazione di un dispositivo al proprio account
Premendo sul pulsante **ADD +** è possibile aggiungere un dispositivo, associandolo al proprio account. Verrà aperto un form da compilare con le informazioni 
richieste:
- **Device Key**: stringa con la chiave del dispositivo: può essere letta tramite un'applicazione dell' **Application Processor**.
- **Name**: nome da assegnare al dispositivo.
- **Location**: è possibile assegnare delle coordinate della localizzazione del dispositivo.
- **Group**: è possibile assegnare un gruppo di appartenenza al dispositivo.

![Add Device](./images/DevicesPage_AddDevice.png){: class="img-doc"}*Form per l'associazione di un dispositivo*

Tramite la pressione del pulsante **CONFIRM** della form di associazione, la piattaforma **MyMote platform** invierà i dati necessari all'associazione con l'utente al dispositivo. Di seguito alcune note importanti per la corretta esecuzione dell'accoppiamento del dispositivo:
* **Connessione Internet**: il dispositivo deve essere connesso ad internet tramite **cavo ethernet** per poter effettuare le prime procedure di accoppiamento. La rete deve disporre di un server DHCP abilitato (di default è disponibile in ogni rete).
* **Computer e Cavo USB**: per poter leggere la **device key** ddel dispositivo è necessario disporre di un PC/MAC collegato alla porta USB del dispositivo X400.
* **Attivazione SIM dati**: i modelli di dispositivo *X400* provvisti di modulo 3G/2G hanno bisogno dell'attivazione della scheda **SIM**. Possono servire fino a due ore di tempo per l'intero processo. L'attivazione è necessaria solo alla prima associazione del dispositivo. Una volta attivata, la **SIM** resta attiva.


## Modifica delle informazioni di un dispositivo
Premendo sul pulsante *Edit* della sezione dettagli, verrà aperta una form con le informazioni del dispositivo:
- **Name**: può essere modificato il nome assegnato durante l'associazione con l'account utente.
- **Location**: possono essere modificate le coordinate della localizzazione fornite dall'utente.
- **Group**: per assegnare il dispositivo ad un determinato gruppo, oppure modificarlo.
- **Delete**: questo pulsante rimuove l'associazione con l'account utente. Per effettuare una nuova associazione è necessario disporre della stringa **device key** descritta nella sezione **Getting Started** ed in **Iomote library**.
