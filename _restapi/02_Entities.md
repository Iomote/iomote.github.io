---
title: Entities
position: 2
---

### **ERROR**
~~~ json
{ "error" : "..." }
~~~

---

### **RESULT**
~~~ json
{ "result" : "..." }
~~~

---

### **GROUP**
~~~ json
{
  "id": "",
  "group_of_user_id": "",
  "name": "",
  "client_name": "",
  "email": "",
  "telephone": ""
}
~~~

---

### **DEVICE**
~~~ json
{  "id": "…", 
  "device_id": "…",
  "device_key": "…",
  "user_id": "…",
  "group_id": "…",
  "name": "…",
  "type": "…",
  "location": "…",
  "connectivity": "",
  "fwversion": "",
  "app_name": "",
  "app_version": "",
  "stat_device_id": "…",
  "ICCID": ""
}
~~~

---

### **DEVICEST**
~~~ json
{ "device": {DEVICE},  "status": ""}
~~~

---

### **DEVICESTATUS** 
~~~ json
{ "connectionState": "" }
~~~

---

### **DEVICESTATS**
~~~ json
{
  "id": "…",
  "stat_of_device_id": "…",
  "msg_tot": 0,
  "msg_current": 0,
  "msg_1": 0,
  "msg_2": 0,
  "msg_3": 0,
  "msg_4": 0,
  "msg_5": 0,
  "msg_6": 0,
  "msg_7": 0,
  "bytes_tot": 0,
  "bytes_current": 0,
  "bytes_1": 0,
  "bytes_2": 0,
  "bytes_3": 0,
  "bytes_4": 0,
  "bytes_5": 0,
  "bytes_6": 0,
  "bytes_7": 0
}
~~~

---

### **FIRMWARE**
~~~ json
{
  "id": "…",
  "type": "…",
  "dateTime": "2018-01-24T16:09:23.1432412+00:00",
  "filepath": "…",
  "name": "…",
  "version": "0.6.3",
  "note": "…",
  "download_key": "…",
  "sig_md5": "…",
  "size": 50000
}
~~~

---

### **APP**
~~~ json
{
  "id": "…",
  "user_id": "…",
  "name": "…",
  "last_app_version_id": "…"
}
~~~

---

### **APPVERSION**
~~~ json
{
  "id": "…",
  "app_id": "…",
  "dateTime": "2017-12-07T16:07:49.8424372+00:00",
  "filepath": "…",
  "name": "…",
  "version": "0.1.2",
  "note": "…",
  "download_key": "…",
  "sig_md5": "…",
  "size": 50000
}
~~~

