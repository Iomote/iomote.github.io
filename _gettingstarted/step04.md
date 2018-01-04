---
title: (Node.JS) Lettura dei messaggi del dispositivo
position: 4
description: Esempio basilare su come ricevere i messaggi inviati dal dispositivo tramite uno script Node.JS
---

Per avere un rapido riscontro sull'effettivo funzionamento dell'architettura, è possibile leggere i dati inviati dal dispositivo tramite un codice di esempio Node.JS. Nel caso non abbiate ancora Node.JS installato nel vostro computer, potete seguire le informazioni sul sito ufficiale [https://nodejs.org](https://nodejs.org)

Una volta installato Node.JS è sufficiente eseguire le seguenti operazioni:
- creare una cartella, per esempio chiamata *iomote-sb-node-example*
- aprire un terminale ed eseguire i comandi dalla cartella appena creata:
	-  `npm install azure`
- creare un file chiamato ***iomoteSbNode.js*** e copiate il codice seguente all'interno del file

~~~ javascript
// Iomote 
// In this example the service bus connection string and queue names are provided using the 
// service bus connection string provided on your  Iomote Dashboard User Settings
// If you don't want to use command line parameters, just paste your connection string on 
// connStr variable initializzation value instead of using command line arguments!
// 
// For Further reference please refer to Microsoft's documentation
// https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-nodejs-how-to-use-queues
//

var azure = require('azure');

var connStr = process.argv[2]; // <<<=== change this init with '<your_service_bus_connection_string>' if you don't want console params
if (!connStr) 
	throw new Error('Must provide connection string');

var queueName = null;
var entityToken = 'EntityPath=';
var entityIndex = connStr.indexOf(entityToken);
var connStrLen = connStr.length;
if(entityIndex > 0) {
  // set a new queueName value:
  queueName = connStr.slice(entityIndex+entityToken.length, connStrLen);
  var serviceBusConnStr = connStr.substr(0, entityIndex-1);
}
if(!queueName) {
  throw new Error('Must provide connection string');
}
console.log("**********************************************************************");
console.log('* Connecting to ', serviceBusConnStr);
console.log('* Queue name ', queueName);
console.log("**********************************************************************");
var serviceBusService = azure.createServiceBusService(serviceBusConnStr);

// This function is responsable of reading messages from service bus queue
var rxQueue = function() {
  serviceBusService.receiveQueueMessage(queueName, function(error, receivedMessage){
    if(!error) {
      console.log("**********************************************************************");
      //console.log('[message] ', receivedMessage);
      if(receivedMessage.body){
        console.log('[message] ', receivedMessage.body);
      }
      if(receivedMessage.customProperties) {
        let userRoute = receivedMessage.customProperties.user_route;
        let mId = receivedMessage.customProperties.mid;
        let devId = receivedMessage.customProperties['iothub-connection-device-id'];
        if(devId) {
          console.log('[device] ', devId);
        }
        if(mId) {
          console.log('[message id] ', mId);
        }
        if(userRoute) {
          console.log('[user route] ', userRoute);
        }
        console.log("**********************************************************************");
      }
    } 
  });
}
// set timed interval so in case your Service Bus client fails, it will register a new Queue Message received callback
var recInterval = setInterval(rxQueue, 25);

~~~
-   sempre da terminale eseguire il comando (sostituendo *YOUR_CONNECTION_STRING_PARAMETER* con la connection string che potete trovare nelle informazioni utente della piattaforma **MyMote Platform**)
	- `node ./iomoteSbNode.js "YOUR_CONNECTION_STRING_PARAMETER"` 
