---
title: Cloud communication
position: 6
---

X400 can be considered an "always on" device, permanently connected with the cloud. The **Iomote Core** manages the connection with the cloud and the messages. All the messages (data and notification) are sent from the application processor to the **Iomote Core**, that is responsible of storing it inside the non-volatile memory and delivering it to the cloud. If there is some issue with the connection is not a problem, because all the messages are stored inside the non volatile memory. So, as soon as the application processor send them to the **Iomote Core**, they are permanently stored until they are not correctly delivered to the cloud. No matter if the network goes down, no matter if the power cable is unplugged, messages are stored inside the flash memory, so, as soon as an internet connection will be available (ethernet or 2G/3G), the device will send all the pending messages in memory.


>**Daily message quota and pending messages**
>
>Pending messages affect ONLY the quota of the day in which they are stored in memory. 
>
>**Example**: if a message is stored in memory today, but the network in not available and it’s sent the day after, the quota for the day after is still 100 messages, PLUS the pending message of the day before. This is because the message is considered “sent” in the moment it passes from application processor to the Iomote Core, no matter when it is received by the cloud. 
{: .warning}


---


### **Data Messages**
~~~ cpp
Iomote.message(char* payload)
~~~
**Parameters**
- **payload**: the message to be sent to cloud. *Payload max length is 3750 bytes*

**Returns**
- **0** in case of success
- **error code** otherwise (refer to [error codes table](/#arduino08_ErrorCodes))


---


### **Notifications**
~~~ cpp
Iomote.notification(int level, char* payload)
~~~
**Parameters**
- **level**: the type of notification you want to send
 - **IOMOTE_NOTIFICATION** used for info messages
 - **IOMOTE_WARNING** used for warning messages
 - **IOMOTE_ALARM** used for alarm messages
- **payload**: the message to be sent to cloud. Payload max length is 100 bytes

**Returns**
- **0** in case of success
- **error code** otherwise (refer to [error codes table](/#arduino08_ErrorCodes))


---


### **Daily messages counter**
To get the counter of the currently daily messages sent by the Iomote Core processor to the cloud:
~~~ cpp
Iomote.messagesLeft(int16_t* left)
~~~
**Parameters**
- **left**: the pointer to your int16_t variable to store data read from Iomote Core (ex: use iomoteClass.messagesLeft(&myVariable); on your code)

**Returns**
- **0** in case of success
- **error code** otherwise (refer to [error codes table](/#arduino08_ErrorCodes))


---


### **Pending messages counter**
To get the counter of the currently queued messages, but not sent yet to the cloud by the Iomote Core processor:
~~~ cpp
Iomote.messagesPending(int16_t* pend)
~~~
**Parameters**
- **pend**: the pointer to your int16_t variable to store data read from Iomote Core (ex: use iomoteClass.messagesPending(&myVariable); on your code)

**Returns**
- **0** in case of success
- **error code** otherwise (refer to [error codes table](/#arduino08_ErrorCodes))
