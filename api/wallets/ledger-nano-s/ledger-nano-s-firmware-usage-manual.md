# Ledger Nano S Firmware Usage Manual

## Overview <a id="overview"></a>

The companion app oneledger is used to demonstrate the basic functionality of the firmware for harmony ledger Nano S. Type ./oneledger help to show the supported commands. -apdu is for debugging purposes only as it logs the communication between host and Ledger Nano S.

`./oneledger help`

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6eNat1O8JeZMLZkGo%2F1.png?alt=media&token=20b2f8d5-41e9-4fcf-9f76-735d122a4789)

## Display Harmony ONE Address in Ledger Nano S <a id="display-harmony-one-address-in-ledger-nano-s"></a>

After initial setup and start running Harmony ONE ledger app, Ledger NanoS will generate a key and store it in the hardware wallet. The address of this key can be displayed through companion app on host using command:

`sudo ./oneledger addr`

Please note a root permission is required to run this command, as it involves USB port communication.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6eafAzXH97HHMgS82%2F2.png?alt=media&token=be8fc2fe-cd53-47fb-8c1d-a21749d85a04)

After running the address command, the following GUI will be displayed on Ledger Nano S LED screen:

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6eizmaPD6JVxDev_H%2F0.jpg?alt=media&token=671e90ce-5629-4e5d-ac51-8d770ac6417a)

There are two buttons on top of Ledger Nano, click the right one to continue \(or click the left one to cancel\). After that, the following address will be shown on Ledger Nano S LED screen:

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6elXYdgYGfK1QwTo9%2F1.jpg?alt=media&token=a780820a-ddb1-48d1-a7ac-603ed3374ced)

As the address is longer than the LED screen, you can use the top two button to shift the address display to the left or side right side. Click both buttons to confirm the address and it should be same as displayed on host console.

The entire process is shown in video below:

## Signing a RAW Transaction using Ledger Nano S <a id="signing-a-raw-transaction-using-ledger-nano-s"></a>

Using the companion application oneledger, Ledger Nanos can process and sign a RAW Harmony block chain transaction \(RLP encoded in hex bytes\) transmitted through the USB interface. Type the following command to sign a transaction:

`sudo ./oneledger signtx e608808252080180940c807574be624ccdff7a7dd64c7add4dc92dd0a9880de0b6b3a764000080`

The argument **e608808252080180940c807574be624ccdff7a7dd64c7add4dc92dd0a9880de0b6b3a764000080** is the RLP encoded RAW transaction which contains the address, amount and shard information.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6ecodfIvjRjcNf1_c%2F3.png?alt=media&token=220719c3-9c6d-4c75-8139-2288cfd9616b)

Click the right button to start signing the transaction

.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6eoZybnHrUZmGwjD6%2F2.jpg?alt=media&token=4e95dce5-a3fc-4fe7-b95c-9de2b9a7038e)

Check and confirm the transfer to address is correct.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6eqqLsb2bDwiMQ2rI%2F3.jpg?alt=media&token=bc38b856-e854-4c5d-97c9-a4e4b7dd3430)

Check and confirm the amount is correct

.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6esS-QaHgW53hL09S%2F4.jpg?alt=media&token=ee9e5941-3b23-4d23-8395-4313c7bf2986)

Check and confirm the source shard ID is correct.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6ewoJRmrEgmFneCVn%2F5.jpg?alt=media&token=691a919a-c841-4d41-bfe9-a3d658ab2e9e)

Check and confirm the destination shard ID is correct`.`

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6eyZo-Z2Dia94jFx3%2F6.jpg?alt=media&token=1da33a34-7a21-4572-8b36-f93e90563a73)

Detailed process is shown in video below:

{% embed url="https://youtu.be/feRpGW1seQI" caption="" %}

