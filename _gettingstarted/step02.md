---
title: Preparazione del dispositivo (associazione account utente)
position: 2
description: Prima accensione del dispositivo
---

Un dispositivo X400 non ancora associato ad alcun account si connette automaticamente all'IoT hub di gestione. Non serve scrivere alcune codice, la connessione viene effettuata automaticamente tramite il cavo ethernet: l'unico vincolo è di poter disporre di un router/access point connesso ad internet con DHCP Server abilitato (generalmente tutti i router sono configurati in tal modo).
Un dispositivo ancora non associato ad alcun account utente può essere considerato come dispositivo "orfano". Le informazioni necessarie per poter effettuare il passaggio all'IoT hub dell'account utente vengono fornite tramite l'IotHub di gestione. Una volta che il dispositivo viene associato all'account utente, l'X400 modificherà automaticamente le sue impostazioni e si sposterà sul nuovo IoT hub. Da questo momento, l'utente potrà scambiare i dati con il dispositivo, ricevere i messaggi, etc...

Per associare il dispositivo al proprio account è necessario inserire la stringa *device key* compilando il form di configurazione del dispositivo della piattaforma **MyMote Platform**, associandolo così al proprio account. La stringa **device key** può essere ricevuta tramite le librerie per Arduino usando il codice riportato in basso. Per ulteriori informazioni riguardo lo sviluppo di applicazioni vedere la sezione dedicata.

* **Nota:** I dispositivi sono precaricati con l'applicazione seguente, ma la riportiamo per ulteriori riferimenti o futuri utilizzi.


~~~ cpp
/*
* Getting started
* Basic example to read Device Key string and print it to Serial Monitor 
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

void setup() 
{
  //  This instruction initializes the board, it's mandatory for any sketch to correctly work with the X400 Cloud Operations!
  Iomote.begin("devKey read", 1,0,0); 
  
  Serial.write("X400 Getting Started!\r\n");
}


void loop() 
{
  //  Check of front button to detect the push event
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
    delay(1000);
  }
}

~~~

Da questo momento in poi, il dispositivo invierà i dati dell'applicazione al service bus dedicato all'utente.
