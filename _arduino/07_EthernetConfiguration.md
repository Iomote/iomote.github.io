---
title: Ethernet configuration
position: 7
---

Sometimes it could be useful to assign static network parameters to **Iomote Core** ethernet interface. **App processor** code can provide all the DHCP related parameters to **Iomote Core** using the following methods.

---

### **Enabled/Disable DHCP Client**
~~~ cpp
void Iomote.netDHCP(bool dhcp_on)
~~~ 
**Parameters**
- **value**: the new status of dhcp client usage
 - **true** if dhcp client should be used
 - **false** if dhcp client should not be used

---

### **IP Address of device on local network**
~~~ cpp
void Iomote.netIP(int n0, int n1, int n2, int n3)
~~~
**Parameters**
- **n0, n1, n2, n3**: the 4 bytes values of desired device IP address


---

### **Subnet**
~~~ cpp
void Iomote.netSubnet(int n0, int n1, int n2, int n3)
~~~
**Parameters**
- **n0, n1, n2, n3**: the 4 bytes values of desired subnet IP address


---

### **Gateway IP**
~~~ cpp
void Iomote.netGateway(int n0, int n1, int n2, int n3)
~~~
**Parameters**
- **n0, n1, n2, n3**: the 4 bytes values of desired gateway IP address


---

### **DNS IP**
~~~ cpp
void Iomote.netDNS(int n0, int n1, int n2, int n3)
~~~ 
**Parameters**
- **n0, n1, n2, n3**: the 4 bytes values of desired DNS IP address


---

### **Apply and Save new configuration**
~~~ cpp
int8_t Iomote.applyNetConfig( )
~~~
**Returns**
- **0** in case of success
- **error code** otherwise (refer to [error codes table](/#arduino08_ErrorCodes))

When **App processor** code executes this method, all the configuration is sent to **Iomote Core**. This new configuration is saved on non-volatile-memory, so each time the device is rebooted, this custom configuration is used.

**NOTE:** this command must be issued after the network commands for the changes to have effects.


---

### **How to restore DHCP Client usage**
Once the device is configured with *static IP parameters*, this behaviour will not change unless App processor overwrites previously provided values. To do this it is sufficient to add this code snippet to a new App processor code:
~~~ cpp
Iomote.setDHCP(true);
Iomote.applyNetConfig();
~~~
