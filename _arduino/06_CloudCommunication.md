---
title: Cloud communication
position: 6
---

X400 can be considered an "always on" device, permanently connected with the cloud. The **Iomote Core** manages the connection with the cloud and the messages. All the messages (data and notification) are sent from the application processor to the **Iomote Core**, that is responsible of storing it inside the non-volatile memory and delivering it to the cloud. If there is some issue with the connection is not a problem, because all the messages are stored inside the non volatile memory. So, as soon as the application processor sends them to the **Iomote Core**, they are permanently stored until they are correctly delivered to the cloud. No matter if the network goes down, no matter if the power cable is unplugged, messages are stored inside the flash memory, so, when an internet connection will be available (ethernet or 2G/3G), the device will send each pending message in memory.

In addition, X400 **Iomote Core** can receive user messages from cloud (cloud to device messages). Up to 10 messages can be stored on non-volatile memory, so **App processor** can read them without worry about _timings_.


>**Pending messages**
>
>Pending messages affect ONLY the quota of the day in which they are stored in memory. 
>
>**Example**: if a message is stored in memory today, but the network in not available and it’s sent the day after, the quota for the day after is still 100 messages, PLUS the pending message of the day before. This is because the message is considered “sent” in the moment it passes from application processor to the Iomote Core, no matter when it is received by the cloud. 
{: .warning}


---


### **Data Messages**
~~~ cpp
int8_t Iomote.sendMessage(char* payload)
~~~
**Parameters**
- **payload**: the message to be sent to cloud. *Payload max length is 3750 bytes*

**Returns**
- **0** in case of success
- **error code** otherwise (refer to [error codes table](/#arduino08_ErrorCodes))


---


### **Notifications**
~~~ cpp
int8_t Iomote.sendNotification(int level, char* payload)
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



### **Pending messages counter**
To get the counter of the currently queued messages, but not sent yet to the cloud by the Iomote Core processor:
~~~ cpp
int8_t Iomote.messagesPending(int16_t* pend)
~~~
**Parameters**
- **pend**: the pointer to your int16_t variable to store data read from Iomote Core (ex: use iomoteClass.messagesPending(&myVariable); on your code)

**Returns**
- **0** in case of success
- **error code** otherwise (refer to [error codes table](/#arduino08_ErrorCodes))


---

### **Check if Cloud to device User Messages are available**
~~~ cpp
bool Iomote.userMessageAvailable()
~~~
Checks if there are any user messages on **Iomote Core** waiting to be sent to **App processor**. 

**Returns**
- **true** in case of messages pending present on non-volatile memory
- **false** if no messages are present on non-volatile memory


---

### **Read User Messages content**
~~~ cpp
int8_t Iomote.userMessageRead(char* buffer)
~~~
Copies the oldest user message content to provided buffer. When **App processor** uses such command, the **Iomote Core** erase the message from non-volatile memory
**Parameters**
- **buffer**: the buffer to use to copy message content. buffer max length should be at least 4096 bytes (the limit of cloud to device user messages size).

**Returns**
- **0** in case of success
- **error code** otherwise (refer to [error codes table](/#arduino08_ErrorCodes))


---

### **Clear all User Messages**
~~~ cpp
int8_t Iomote.userMessageClearAll()
~~~
Forces the erasing of all messages present on **Iomote Core** non-volatile memory, without reading them.

**Returns**
- **0** in case of success
- **error code** otherwise (refer to [error codes table](/#arduino08_ErrorCodes))


---