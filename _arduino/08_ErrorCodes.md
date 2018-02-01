---
title: Error Codes
position: 8
---

| Error Name | Value | Description |
| ----------------- |:------:| ----------------------- |
| IOMOTE_ERR_TIMEOUT | -1 | No response from **Iomote Core** (temporarily busy) |
| IOMOTE_ERR_DATA | -2 | Provided **data parsing** error |
| IOMOTE_ERR_MSG_SIZE | -3 | IotHub Message buffer cannot accept data: **message size** limit reached |
| IOMOTE_ERR_MSG_LIMIT | -4 | **Daily message limit** on **Iomote Core** reached! |
| IOMOTE_ERR_PAYLOAD | -5 | **Payload length** not compliant with command |
| IOMOTE_ERR_DHCP_VAL | -6 | Errors on data provided with **DHCP Settings**|
| IOMOTE_ERR_STORAGE_FULL | -7 | Storage on **Iomote Core** is full |
| IOMOTE_ERR_STORAGE_WR | -8 | Cannot write data on **Iomote Core** storage, but it is not full! |
| ... | | |
| IOMOTE_ERR_MEMORY | -123 | Internal memory error on **Iomote Core** |
| IOMOTE_ERR_CHECKSUM | -126 | **Checksum** calculation error: data not valid |
| IOMOTE_ERR_UNKNOWN | -127 | **Generic unknown** error |

