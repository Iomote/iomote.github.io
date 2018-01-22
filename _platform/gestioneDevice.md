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


## Modifica delle informazio di un dispositivo
Premendo sul pulsante *Edit* della sezione dettagli, verrà aperta una form con le informazioni del dispositivo:
- **Name**: può essere modificato il nome assegnato durante l'associazione con l'account utente.
- **Location**: possono essere modificate le coordinate della localizzazione fornite dall'utente.
- **Group**: per assegnare il dispositivo ad un determinato gruppo, oppure modificarlo.
- **Delete**: questo pulsante rimuove l'associazione con l'account utente. Per effettuare una nuova associazione è necessario disporre della stringa **device key** descritta nella sezione **Getting Started** ed in **Iomote library**.
