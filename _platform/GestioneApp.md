---
title: Gestione app
position: 5
---

Nella pagina **Alarms** è possibile gestire le Applicazioni sviluppate dall'utente.
Sono presiste due sezioni:
- **Sezione centrale**: è visualizzato l'elenco di tutte le applicazioni create dall'utente.
- **Sezione dettagli**: è visualizzato l'elenco dele varie versioni caricate.

![Apps](./images/AppsPage.png){: class="img-doc"}

L'utente può creare delle applicazioni premendo sul pulsante **ADD +** della sezione centrale. A questo punto si può scegliere il nome dell'applicazione. In questo modo si è creato un contenitore per tutte le varie versioni della medesima applicazione che si vuole creare.

Ogni versione di applicazione deve essere fornita tramite un file **.bin** compilato per l'**Application Processor** tramite l'ambiente di sviluppo **Arduino IDE** o equivalenti. Per caricare una nuova versione del file, premere sul pulsante **ADD +** della sezione dettagli.

![Apps](./images/AppsPage_AddVersion.png){: class="img-doc"}


### Dove trovare i file .bin compilati

Se si utilizza l'ambiente **Arduino IDE** basta andare sul menu **Sketch -> Esporta sketch compilato**. Il file verrà compilato e copiato nella cartella del progetto. 
Per aprire la cartella del progetto andare sul menu **Sketch -> Apri cartella dello sketch**.

In **Visual studio code** invece, aprire il file *arduino.json* all'interno della cartella *.vscode* del progetto. Inserire la stringa
`"output": "./build"` all'interno del file json di configurazione. Tutti i file di compilazione verranno generati all'interno di tale cartella, compreso il file **.bin** da utilizzare nella **MyMote platform**.
