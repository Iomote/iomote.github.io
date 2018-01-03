---
title: Compilazione del codice di esempio
position: 3
description: Scrittura di un programma demo
---

Per poter inviare dei messaggi dal dispositivo verso il cloud, è necessario scrivere uno sketch con l'ambiente di sviluppo Arduino IDE. A titolo di esempio riportiamo un primo codice che invia dati casuali alla pressione del pulsante utente.

*Copiare il contenuto seguente nell'editor dell'ambiente di sviluppo*
~~~ C++
#include <iomoteClass.h>

#define SerialDebug   SerialUSB 

void setup() {
	//	This instruction initializes the board, it's mandatory for any sketch to correctly work with the X400 Cloud Operations!
	Iomote.begin("getting started",0,0,1);	
	
	SerialDebug.write("X400 Getting Started!\r\n");
}


void loop() {
	//	Check of front button to detect the push event
	if(Iomote.SwitchRead() == 0)
	{
		//	Two random number are created and are sent to the Iot Hub
		int16_t randomData = rand();
		// 	Adding first number to the JSON string to send 
		int8_t dataResult = Iomote.append((char*)"random data 1", randomData);	
		randomData = rand();
		//	Adding second number to the JSON string
		dataResult += Iomote.append((char*)"random data 2", randomData);
		//	The JSON is finalized adding the timestamp, so the string is ready 
		//	to be sent.
		dataResult += Iomote.object();
		if(dataResult == 0)
		{
			SerialDebug.write("Data added to queue...\r\n");
			//	With the sendData command the data is put in a queue, and wil be 
			//	sent to IoT Hub. 
			int8_t sendResult = Iomote.send();
			if(sendResult == 0)
			{
				SerialDebug.write("Data correctly enqueued and ready to be sent!\r\n");
			}
			else
			{
				SerialDebug.write("Unable to send data now! Result: ");
				SerialDebug.println(sendResult);
			}
		}
		else
		{
			SerialDebug.write("Unable to add data! Result: ");
			SerialDebug.println(dataResult);
		}
		delay(1000);
	}
}
~~~

Una volta copiato il codice, è necessario collegare il dispositivo X400 al computer tramite un USB. Il computer riconoscerà il dispositivo ed installerà i driver necessari (emulazione di porta seriale tramite USB).

Dopo che il sistema operativo avrà correttamente configurato il dispositivo connesso, nell'ambiente di sviluppo è necessario impostare la porta seriale di comunicazione: andare nel menu *Strumenti -> Porta: xxx* e selezionare la porta di comunicazione del dispositivo (per maggiori info si prega di seguire le guide disponibili su [www.arduino.cc](http://www.arduino.cc)).
Per aggiornare il firmware bisogna premere l'icona "carica" (freccia destra).

Una volta terminato il caricamento dell'applicazione, il dispositivo attenderà la pressione del pulsante utente per inviare verso il cloud il messaggio con i dati casuali generati via codice.

*Nota: per avere un riscontro sull'esecuzione del codice, è possibile aprire il monitor seriale nell'ambiente di sviluppo: menu Strumenti -> Monitor Seriale*
