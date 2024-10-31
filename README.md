# STM32WBA-BLE-Encrypted-Advertising

Demonstrate STM32WBA acting as BLE central and GATT client with p2pClient_EAD_Ext and GAP peripheral and GATT server with p2pServer_EAD_Ext.

p2pClient_EAD_Ext application scans and connects to p2pServer_EAD_Ext device.
p2pServer_EAD_Ext application uses a new characteristic "Encrypted Data Key Material" to encrypt advertising data. 
Once connected and bonded, p2pClient_EAD_Ext can read the "Encrypted Data Key Material" characteristic of the p2pServer_EAD_Ext and uses it to decrypt encrypted advertising data.     

## Setup
These applications are running on two **NUCLEO-WBA55CGA boards**. 
Applications are derived from BLE_p2pClient_Ext and BLE_p2pServer_Ext applications for use of extended advertising.
Open a VT100 terminal on Central and Peripheral side (ST Link Com Port, @115200 bauds).
At startup, devices are initialized.
 - The peripheral device starts advertising with Encrypted advertising data. Encrypted Data are received by the central and cannot be decrypted if keys are not stored in RAM.
 On Central:
 - Press B1: central starts scanning. Scan is stopped if a p2pServer_EAD_Ext device is detected.
 - Press B3: central initiates a connection. Discovery of service and characteristics. Exchange of max ATT_MTU, pairing and bonding.
 when devices are connected: 
 - Press B2: initiates a disconnection 
 when devices are not connected:
 - Press B1 to launch a scan. Encrypted Data are received and decrypted if keys are stored in RAM.

## Application description
These applications are based on P2P server Ext and P2P client Ext from STM32CubeWBA package v1.4.1.   

On peripheral: 
- At reset and on disconnection, device starts advertising. It uses "Encrypted Data Key Material" to encrypt advertising data.

On central:
 - Press B1 to launch a scan. Scan is stopped if a p2pServer_EAD_Ext device is detected.
 - Press B3 to initiate a connection. Discovery of service and characteristics. Exchange of max ATT_MTU, pairing and bonding.
 - Press B2 to initiate a disconnection.
 - Press B1 to launch a scan. Encrypted Data are received and decrypted.

## Troubleshooting

**Caution** : Issues and the pull-requests are **not supported** to submit problems or suggestions related to the software delivered in this repository. The STM32WBA-BLE-Encrypted-Advertising example is being delivered as-is, and not necessarily supported by ST.

**For any other question** related to the product, the hardware performance or characteristics, the tools, the environment, you can submit it to the **ST Community** on the STM32 MCUs related [page](https://community.st.com/s/topic/0TO0X000000BSqSWAW/stm32-mcus).