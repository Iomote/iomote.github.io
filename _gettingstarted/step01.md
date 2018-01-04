---
title: Prerequisiti
position: 1
---

Prima di continuare è necessario effettuare le seguenti operazioni:

-   Una volta acquistato il kit del dispositivo X400, il team di Iomote creerà un account per la **MyMote Platform**. Le informzioni di tale account verranno comunicate via e-mail.
-   Installare l'ambiente di sviluppo **Arduino IDE** nel computer (*Per gli utenti Windows 10 si consiglia di scaricare l'installer ed evitare la versione del windows store*). Puoi trovare tutti i riferimenti (inclusi tutorials ed esempi) sul sito [www.arduino.cc](http://www.arduino.cc). Una volta installato l'ambiente di sviluppo bisogna aggiungere le **librerie software per il gateway X400**:
    1. Aprire il menu *File -> Impostazioni*
    2. Nel tab delle impostazioni, alla voce *URL aggiuntive per il Gestore schede* inserire `https://github.com/iomote/arduino-ide-bsp/raw/master/package_iomote_index.json` (separato da virgola se ci sono già degli indirizzi) e confermare le modifiche tramite il pulsante **OK**
    3. Aprire il **Gestore schede** (menu *Strumenti -> Scheda:xxx -> Gestore schede*)
    4. Installare il pacchetto **Arduino SAMD Boards (32.bits ARM Cortex-M0+) by Arduino**
    5. Installare il pacchetto **Iomote X400 by Iomote**
    6. Aprire il **Gestore librerie** (menu *Sketch -> #include librerie -> Gestore librerie*)
    7. Installare la libreria **RTCZero by Arduino**
    8. Selezionare la scheda X400 dal menu *Strumenti -> Scheda:xxx -> Iomote X400*
    9. A questo punto l'ambiente di sviluppo è pronto: è possibile sviluppare *sketch* per il dispositivo X400 tramite **Arduino IDE**.
