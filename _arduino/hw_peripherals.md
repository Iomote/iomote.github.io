---
title: Periferiche Hardware
position: 4
description: Utilizzo delle periferiche hardware tramite le funzioni della classe Iomote
---

### Pulsante Utente
~~~ cpp
Iomote.SwitchRead()
~~~
Restituisce lo stato del segnale collegato al pulsante utente
* 0 in caso di pulsante premuto
* 1 altrimenti

---
### Ingressi analogici (connettore a vite) 
~~~ cpp
Iomote.AnalogRead_1() 

Iomote.AnalogRead_2()
~~~
Restituisce il valore convertito degli ingressi analogici condizionati (connettore a vite).
* AnalogRead_1 legge l'ingresso 4/20 mA
* AnalogRead_2 legge l'ingresso 0/10 V

I valori restituiti sono in virgola mobile `float`.

---
### Ingressi Digitali (connettore a vite)
~~~ cpp
Iomote.DigitalRead_1() 

Iomote.DigitalRead_2() 
~~~
Restituisce il valore degli ingressi digitali condizionati (connettore a vite)

---
### Uscita digitale collettore aperto (connettore a vite)
~~~ cpp
Iomote.SetDigitalOutput(value)
~~~
Imposta un nuovo valore dell'uscita digitale collettore aperto (connettore a vite)

~~~ cpp
Iomote.ToggleDigitalOutput() 
~~~
Inverte il valore dell'uscita digitale collettore aperto (connettore a vite)

---
### Relay
~~~ cpp
Iomote.RelayWrite(value)
~~~
Imposta un nuovo stato del relay

---
### LED Utente
Il LED utente non ha alcun metodo specifico nella classe Iomote. E' sufficiente usare il **pin 7** tramite la funzione *digitalWrite* oppure *analogWrite* (PWM) come descritto ampiamente nella documentazione ufficiale di Arduino.

---
### Porte Seriali RS232 / RS485 
Il device Iomote X400 integra una porta seriale industriale configurabile come **RS232** oppure **RS485**. Si può configurare tale porta fornendo il parametro mode alla funzione SerialBegin

~~~ cpp
Iomote.SerialBegin(baudrate, mode)
~~~
La funzione inizializza la porta seriale con il baudrate fornito. La modalità sarà data dal parametro mode usando i valori di seguito riportati:
* RTS_CTS_OFF → porta seriale configurata come RS232 con i soli segnali TX ed RX
* RTS_CTS_ON → porta seriale configurata come RS232 con i segnali TX, RX, RTS e CTS
* RS485 → porta seriale configurata come RS485.

**Nota:** i segnali RS232 e quelli RS485 sono riportati sui pin dei connettori a vite. E' necessario consultare la documentazione per poter collegare i segnali correttamente.

#### Funzioni di utilizzo della porta seriale RS232/RS485
Le funzioni per usare la porta seriale sono equivalenti a quelle fornite dalla classe Serial di Arduino:

| Arduino Reference |     | Iomote class equivalent |
| ----------------- |:------:| ----------------------- |
| `Serial.end()` | → | `Iomote.SerialEnd()` |
| `Serial.available()` | → | `Iomote.SerialAvailable()` | 
| `Serial.read()` | → | `Iomote.SerialRead()` |
| `Serial.peek()` | → | `Iomote.SerialPeek()` |
| `Serial.end()` | → | `Iomote.SerialEnd()` |
| `Serial.available()` | → | `Iomote.SerialAvailable()` |
| `Serial.read()` | → | `Iomote.SerialRead()` |
| `Serial.peek()` | → | `Iomote.SerialPeek()` |


Per quanto riguarda la funzione `Serial.write()` ci sono 3 metodi disponibili:
~~~ cpp
Iomote.SerialWrite(const uint8_t data);
Iomote.SerialWrite(const char *str);
Iomote.SerialWrite(const uint8_t *buffer, size_t size);
~~~
