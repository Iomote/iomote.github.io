---
title: Sviluppare Applicazioni con Microsoft Visual Studio Code
position: 8
description: Guida alla preparazione dell'ambiente di sviluppo Visual Studio Code per sviluppare Applicazioni per l'Application Processor del dispositivo X400
--- 

Microsoft Visual Studio Code è un ambiente di sviluppo multipiattaforma opensource. Tramite l'utilizzo di estensioni è possibile ampliare le capacità di tale software.
Nel nostro caso, utilizzando l'estensione *Arduino for Visual Studio Code* di Microsoft, è possibile scrivere e compilare codice per Arduino.

### Preparazione di Microsoft Visual Studio Code
Per installare Visual Studio Code è sufficiente recarsi alla [pagina del prodotto](https://code.visualstudio.com/) e seguire la guida nel sito.

Prima di poter utilizzare l'estensione per Arduino, è necessario installare anche l'ambiente di sviluppo **Arduino IDE**. Per maggiori informazioni a riguardo si prega di verificare la sezione *Getting Started*.

Una volta installato Arduino IDE, *aprire Visual Studio Code* ed installare l'estensione *Arduino for Visual Studio Code*:
* Aprire il menu *Visualizza -> Estensioni*
* Nella barra di ricerca scrivere **Arduino** e selezionare la casella **Arduino for Visual Studio Code** di *Microsoft*
* Installare tale estensione e se necessario riavviare il programma


### Configurare un progetto per Iomote X400 **Application Processor**
Per creare un nuovo progetto di Applicazione per **Application Processor** in Visual Studio Code, aprire una cartella tramite il menu *File -> Apri Cartella..*. Se necessario creare una cartella prima di aprirla da Visual Studio Code.

Ora aprire il riquadro dei comandi (tasto F1) e digitare il comando *Arduino: Initialize*. Verrà richiesto di creare un file di sketch, decidere un nome e proseguire.
La scelta della scheda deve essere **Iomote X400**. Un progetto vuoto è stato creato.

Importare la libreria **iomoteClass** nel progetto
* F1
* *Arduino: Library Manager*
* Cercare la libreria **iomoteClass** ed **includerla** nel progetto tramite l'apposito pulsante.

A questo punto il progetto può essere scritto tramite **Visual Studio Code**. Ogni riferimento ai comandi relativi all'estensione vscode-arduino sono disponibili nella pagina ufficiale.


