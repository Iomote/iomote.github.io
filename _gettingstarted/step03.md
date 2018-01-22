---
title: Compilazione del codice di esempio
position: 3
description: Scrittura di un programma demo
---

Per poter inviare dei messaggi dal dispositivo verso il cloud, è necessario scrivere uno sketch con l'ambiente di sviluppo Arduino IDE. A titolo di esempio riportiamo un primo codice che invia dati casuali alla pressione del pulsante utente.

*Copiare il contenuto seguente nell'editor dell'ambiente di sviluppo*
~~~ cpp
/*
* Getting started
* Basic example to 
*  - read Device Key string and print it to Serial Monitor 
*  - send 2 random numbers as data to the cloud when the button is pressed.
*
* License: MIT license
*
* THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
* IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
* FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
* AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
* LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
* OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
* SOFTWARE.
*/
#include <iomoteClass.h>

#define Serial   SerialUSB 

char devKeyBuff[65]; // 64 bytes are used for devKey value, 1 byte for terminator char
char buff[3750]; // max message size is 3750 bytes

void setup() 
{
	//	This instruction initializes the board, it's mandatory for any sketch to correctly work with the X400 Cloud Operations!
	Iomote.begin("getting started", 1,0,0);	
	
	Serial.write("X400 Getting Started!\r\n");
}

void loop() 
{
	//	Check of front button to detect the push event
	if(Iomote.SwitchRead() == 0)
	{
		memset(devKeyBuff, '\0', 65);
		// Read devKey from device:
		int8_t result = Iomote.devKeyRead(devKeyBuff);
		if(result == 0)
		{
			Serial.write("devKey: ");
			Serial.println(devKeyBuff);
		}
		else
		{
			Serial.write("Unable to send data now! Result: ");
			Serial.println(result);
		}

		memset(buff, '\0', 3750);
		//	Two random number are created and are sent to the Iot Hub
		int16_t randomData1 = rand();
		int16_t randomData2 = rand();
		time_t now = Iomote.rtc.getEpoch();
		sprintf(buff, "{\"rand_1\":%d,\"rand_2\":%d,\"ts\":%u}", randomData1, randomData2, now);

		//	With the sendData command the data is put in a queue, and wil be 
		//	sent to IoT Hub. 
		int8_t sendResult = Iomote.message(buff);
		if(sendResult == 0)
		{
			Serial.write("Data correctly enqueued and ready to be sent!\r\n");
		}
		else
		{
			Serial.write("Unable to send data now! Result: ");
			Serial.println(sendResult);
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
