---
title: Codici di errore
position: 6
description: Codici di errore in risposta ai comandi della classe Iomote
---

| Error Name | Value | Description |
| ----------------- |:------:| ----------------------- |
| ARD_ERR_TIMEOUT | -1 | No response from **Iomote Core** (temporarily busy) |
| ARD_ERR_DATA | -2 | Provided **data parsing** error |
| ARD_ERR_MSG_SIZE | -3 | IotHub Message buffer cannot accept data: **message size** limit reached |
| ARD_ERR_MSG_LIMIT | -4 | **Daily message limit** on **Iomote Core** reached! |
| ARD_ERR_PAYLOAD | -5 | **Payload length** not compliant with command |
| ARD_ERR_DHCP_VAL | -6 | Errors on data provided with **DHCP Settings**|
| ARD_ERR_STORAGE_FULL | -7 | Storage on **Iomote Core** is full |
| ARD_ERR_STORAGE_WR | -8 | Cannot write data on **Iomote Core** storage, but it is not full! |
| ... | | |
| ARD_ERR_MEMORY | -123 | Internal memory error on **Iomote Core** |
| ARD_ERR_CHECKSUM | -126 | **Checksum** calculation error: data not valid |
| ARD_ERR_UNKNOWN | -127 | **Generic unknown** error |

