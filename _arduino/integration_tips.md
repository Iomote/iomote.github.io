---
title: Integrazione con librerie esterne
position: 7
description: Suggerimenti sull'integrazione di librerie di terze parti con la Iomote class
--- 


### Gestione dell'inizializzazione hardware
Dato che il dispositivo Iomote X400 deve essere inizializzato correttamente all'avvio di ogni Applicazione in esecuzione sull'**Application Processor**, suggeriamo fortemente di inserire la funzione `Iomote.begin(...)` come primo comando della funzione `setup()` di Arduino.
Tutte le inizializzazioni delle librerie e dell'hardware di terze parti possono essere inserite dopo, riconfigurando i segnali già impostati dalla classe Iomote se necessario.

Per esempio, se l'applicazione deve inizializzare un sensore digitale di temperatura ed umidità connesso al pin 6, suggeriamo di procedere come segue:
* Usare la funzione `Iomote.begin(...)` per inizializzare l'hardware correttamente
* Usare poi le funzioni fornite nella libreria del sensore per inizializzare il pin 6 correttamente (per esempio `devXYZ.init(6);`)

---
### Debug Monitor
#### Definizione dell'oggetto Serial
Molti esempi online per Arduino utilizzano l'oggetto `Serial` come interfaccia principale di debug. Affinchè il dispositivo X400 (oppure qualunque Arduino basato su Cortex-M0+) possa usare la terminologia **Serial** come interfaccia principale di debug è sufficiente definirla nel codice dello sketch:
~~~ cpp
#define Serial SerialUSB // use Serial1 for external connector pins UART or SerialUSB for CDC USB Uart
~~~
E' quindi possibile definire **Serial** come **SerialUSB** oppure **Serial1** a seconda delle necessità dell'utente, e poi usare la denominazione *Serial* all'interno del codice.

#### Attendere la connessione del PC alla porta SerialUSB
In caso si sia scelto di usare la porta SerialUSB, bisogna considerare alcuni aspetti peculiari di tale interfaccia. Essendo una porta UART emulata tramite USB CDC, è possibile attendere che il PC sia effettivamente connesso tramite il cavo USB.

Infatti è possibile verificare che l'oggetto `SerialUSB` sia stato inizializzato, e che quindi non sia nullo.

Di seguito è riportato un esempio di codice che tiene conto anche di un timeout in modo da evitare che l'applicazione attenda in eterno la connessione del PC e che quindi possa comunque funzionare anche in assenza di esso.


~~~ cpp
SerialUSB.begin(115200);
int maxSerialWaiting = 2000; // up to 2 seconds...
while((!SerialUSB) && (maxSerialWaiting > 0))
{
	maxSerialWaiting--;
	delay(1);
}
~~~

Tale frammento di codice può essere inserito per esempio nella funzione `setup()` di Arduino. In questo modo l'**Application Processor** attenderà fino a 2 secondi circa, dopodichè procederà con l'esecuzione del resto dell'applicazione.
