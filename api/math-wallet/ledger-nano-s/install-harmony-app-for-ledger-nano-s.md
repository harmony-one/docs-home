# Install Harmony App for Ledger Nano S

## Overview

The Nano S is a hardware wallet created by Ledger. A hardware wallet stores the private keys to Harmony tokens on a separate device, making it much harder for malicious parties to steal them. In fact, the private keys never leave the Nano S itself, so they will remain secure even if the device is connected to a compromised computer. As long as you follow best practices when using your Nano S, it is virtually impossible for an attacker to steal your funds.

## Set up your Ledger Nano S

_Let's make sure your hardware wallet ready to use._

1. [Initialize](https://support.ledgerwallet.com/hc/en-us/articles/360000613793) your Ledger Nano S. This gets the hardware wallet set up and ready to use.

{% embed url="https://youtu.be/JlojlZiVK8E" caption="" %}

1. Download [Ledger Live](https://support.ledgerwallet.com/hc/en-us/articles/360006395553/) onto your computer. Ledger Live is the app you use to manage your Ledger device.  Please follow the official installation instruction [here](https://support.ledger.com/hc/en-us/articles/360006395553). 
2. [Install the latest firmware](https://support.ledgerwallet.com/hc/en-us/articles/360002731113) on your Nano S. This ensures compatibility with the Harmony app. The latest firmware is version 1.6.0 .   

{% embed url="https://youtu.be/\_5CymmI4BTQ" caption="" %}

At this point, you're ready to install apps on your Ledger Nano S. Remember to store your 24-word recovery phrase in a safe place, because you'll need it to recover your funds if your device is lost or damaged.

## Install Ledger Nano S Firmware In Debugging Mode

_This is ONLY for wallet developers / testers._  

1. Download Ledger firmware app.hex from [here](https://s3-us-west-1.amazonaws.com/pub.harmony.one/release/ledger_firmware/ver1_app.hex) .
2. Place the downloaded firmware file _**ver1\_app.hex**_ in the current working directory.
3. Set up the python loader 

```text
[sudo] pip install -U setuptools
[sudo] pip install virtualenv

#linux dependencies for ledgerblue module  
#sudo apt install libudev1 libudev-dev libusb-1.0-0-dev

virtualenv -p python3 venv
source venv/bin/activate
pip install ledgerblue
or pip install git+https://github.com/LedgerHQ/blue-loader-python.git
```

1. Run the following command to load the firmware to Ledger Nano S. 

```text
sudo ./venv/bin/python -m ledgerblue.loadApp --appFlags 0x40 --path "44'/1023'"  --curve secp256k1 --tlv --targetId 0x31100004 --delete --fileName app.hex --appName One --appVersion 0.0.1 --dataSize 0 --icon 01ffffff00ffffff00ffffffffffffc7e1bbcdbbddbbcdbbc50bd8a3ddbbddbbddb3edc7e3ffffffff
```



## Display the Harmony ONE address for Ledger Nano S

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lp17W8qGssyWUeQC8Hm%2F-Lp1QqkoLZa7pg6QMFeO%2F1assets_-LlYdMT-Wp5uYwcF_tMW.jpg?alt=media&token=32fe24fd-f99c-48d3-84a6-48e1e3664fc6)

There are two buttons on top of Ledger Nano, click the right one to continue \(or click the left one to cancel\). After that, the following address will be shown on Ledger Nano S LED screen:‌

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lp17W8qGssyWUeQC8Hm%2F-Lp1QtQgDJ6cR36TkYqq%2F2.jpg?alt=media&token=3c767945-33b3-432f-a959-faaba7f3d010)

As the address is longer than the LED screen, you can use the top two button to shift the address display to the left or side right side. Click both buttons to confirm the address and it should be same as displayed on PC/Mac terminal.‌

The entire process is shown in video below:

{% embed url="https://www.youtube.com/watch?v=m5RLYGWosuk&feature=youtu.be" %}

## Token transfer using Ledger Nano S

The LED display on Nano S is shown as below :‌

Click the right button to start signing the transaction

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lp1RBqYpGIEBEHFW8oF%2F-Lp1fC7Z1fvYt5C5Rjal%2F1.jpg?alt=media&token=82958d36-4e76-4f8a-96b0-242b5facaea8)

Check and confirm the transfer to address is correct.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6eqqLsb2bDwiMQ2rI%2F3.jpg?alt=media&token=bc38b856-e854-4c5d-97c9-a4e4b7dd3430)

Check and confirm the amount is correct.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6esS-QaHgW53hL09S%2F4.jpg?alt=media&token=ee9e5941-3b23-4d23-8395-4313c7bf2986)

Check and confirm the source shard ID is correct.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6ewoJRmrEgmFneCVn%2F5.jpg?alt=media&token=691a919a-c841-4d41-bfe9-a3d658ab2e9e)

Check and confirm the destination shard ID is correct.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6eyZo-Z2Dia94jFx3%2F6.jpg?alt=media&token=1da33a34-7a21-4572-8b36-f93e90563a73)

Detailed process is shown in video below:

{% embed url="https://youtu.be/feRpGW1seQI" caption="" %}

## 

