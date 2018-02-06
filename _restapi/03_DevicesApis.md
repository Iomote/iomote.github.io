---
title: Devices APIs
position: 3
---

Following is a list of all available APIs related to **devices management**

---

### **Get all devices with connection status**
- type: **GET**
- endpoint: *api/user/{userid}/{webapi_key}/devices*
- result: `ERROR` or `[{DEVICEST}, …]`

---
 
### **Get a device with connection status**
- type: **GET**
- endpoint: *api/user/{userid}/{webapi_key}/devices/{deviceid}*
- result: `ERROR` or `[{DEVICEST}, …]`

---
 
### **Get a device connection status**
- type: **GET**
- endpoint: *api/user/{userid}/{webapi_key}/devices/{deviceid}/status*
- result: `ERROR` or `DEVICESTATUS`    	

---
 
### **Get a device activity statistics**
- type: **GET**
- endpoint: *api/user/{userid}/{webapi_key}/devices/{deviceid}/stat*
- result: `ERROR` or `DEVICESTATS`	

---
 
### **Get all devices from a group**
- type: **GET**
- endpoint: *api/user/{userid}/{webapi_key}/devices/group/{groupid}*
- result: `ERROR` or `[{DEVICE}, …]`
 
---

### **Send new app to a device**
- type: **POST**
- endpoint: *api/user/{userid}/{webapi_key}/devices/{deviceid}/newapp/{appid}/{appversionid}*
- result: `ERROR` or `RESULT`
 
---

### **Send new firmware to a device**
- type: **POST**
- endpoint: *api/user/{userid}/{webapi_key}/devices/{deviceid}/newfirmware/{firmwareid}/NOW*
- result: `ERROR` or `RESULT`      	
