---
title: (.NETCore) Lettura dei messaggi del dispositivo
position: 5
description: Esempio basilare su come ricevere i messaggi inviati dal dispositivo tramite uno script .NETCore
---


Per avere un rapido riscontro sull'effettivo funzionamento dell'architettura, è possibile leggere i dati inviati dal dispositivo tramite un codice di esempio .NETCore. Nel caso non abbiate ancora .NETCore SDK installato nel vostro computer, potete seguire le informazioni sul sito ufficiale [Microsoft website](https://www.microsoft.com/net/download/windows).

Una volta installato .NETCore è sufficiente eseguire le seguenti operazioni:
- creare una cartella, per esempio chiamata *iomote-sb-dotnetcore-example*
- aprire un terminale ed eseguire i comandi dalla cartella appena creata per creare una nuova applicazione Console .NET Core
    - `dotnet new console`
- ora installate i pacchetti per la comunicazione client con il ServiceBus
    - `dotnet add package Microsoft.Azure.ServiceBus`
- copiate il contenuto seguente nel file *"Program.cs"* (sostituendo *YOUR_CONNECTION_STRING_PARAMETER* con la connection string che potete trovare nelle informazioni utente della piattaforma **MyMote Platform**)

```cs

using System;
using System.Threading.Tasks;
using System.Threading;
using System.Text;
using Microsoft.Azure.ServiceBus;

namespace iomote_sb_dotnetcore_example
{
    class Program
    {
        // Parse connection string parameters to get queue name and connection string values...
        static string iomoteSbConnectionString = "YOUR_CONNECTION_STRING_PARAMETER";
        static string ServiceBusConnectionString = null;
        static string QueueName = null;
        static IQueueClient queueClient;

        static void Main(string[] args)
        {
            Console.WriteLine("********************************************************************\r\nIomote Service Bus C# Example\r\n********************************************************************");
            
            int queuePos = iomoteSbConnectionString.IndexOf(";EntityPath=");
            QueueName = iomoteSbConnectionString.Substring(queuePos+12);
            ServiceBusConnectionString = iomoteSbConnectionString.Substring(0, queuePos);

            Console.WriteLine("Connection string: " + ServiceBusConnectionString);
            Console.WriteLine("Queue Name: " + QueueName);
            Console.WriteLine("********************************************************************");
            // https://github.com/Azure/azure-service-bus/tree/master/samples/DotNet/Microsoft.Azure.ServiceBus/BasicSendReceiveUsingQueueClient
            MainAsync(args).GetAwaiter().GetResult();
        }

        static async Task ProcessMessagesAsync(Message message, CancellationToken token)
        {
            // Process the message
            object deviceSender = null;
            object body = null;

            Console.WriteLine("********************************************************************");
            if(message.UserProperties.TryGetValue("iothub-connection-device-id", out deviceSender))
            {
                Console.WriteLine($"Received message from {deviceSender.ToString()}");
            }
            if (message.Body != null)
            {
                body = Encoding.UTF8.GetString(message.Body);
                Console.WriteLine($"Message application Data: {body.ToString()}");
            }
            Console.WriteLine("********************************************************************");
            // Complete the message so that it is not received again.
            // This can be done only if the queueClient is opened in ReceiveMode.PeekLock mode (which is default).
            await queueClient.CompleteAsync(message.SystemProperties.LockToken);
        }

        // Use this Handler to look at the exceptions received on the MessagePump
        static Task ExceptionReceivedHandler(ExceptionReceivedEventArgs exceptionReceivedEventArgs)
        {
            Console.WriteLine($"Message handler encountered an exception {exceptionReceivedEventArgs.Exception}.");
            return Task.CompletedTask;
        }

        static void RegisterOnMessageHandlerAndReceiveMessages()
        {
            // Configure the MessageHandler Options in terms of exception handling, number of concurrent messages to deliver etc.
            var messageHandlerOptions = new MessageHandlerOptions(ExceptionReceivedHandler)
            {
                // Maximum number of Concurrent calls to the callback `ProcessMessagesAsync`, set to 1 for simplicity.
                // Set it according to how many messages the application wants to process in parallel.
                MaxConcurrentCalls = 4,

                // Indicates whether MessagePump should automatically complete the messages after returning from User Callback.
                // False value below indicates the Complete will be handled by the User Callback as seen in `ProcessMessagesAsync`.
                AutoComplete = false
            };

            // Register the function that will process messages
            queueClient.RegisterMessageHandler(ProcessMessagesAsync, messageHandlerOptions);
        }

        static async Task MainAsync(string[] args)
        {
            queueClient = new QueueClient(ServiceBusConnectionString, QueueName);

            // Register QueueClient's MessageHandler and receive messages in a loop
            RegisterOnMessageHandlerAndReceiveMessages();
            
            Console.WriteLine("********************************************************************\r\nPress any key to exit after receiving all the messages\r\n********************************************************************\r\n");
            Console.ReadKey();

            await queueClient.CloseAsync();
        }
    }
}


```

- dal terminale eseguire il comando
    - `dotnet restore`
- ora è possibile eseguire l'applicazione eseguendo
    - `dotnet run`