# Install and Setup

## Set up your Ledger Nano S

_Let's make sure your hardware wallet ready to use._

1. [Initialize](https://support.ledgerwallet.com/hc/en-us/articles/360000613793) your Ledger Nano S. This gets the hardware wallet set up and ready to use.

{% embed url="https://youtu.be/JlojlZiVK8E" %}

1. Download [Ledger Live](https://support.ledgerwallet.com/hc/en-us/articles/360006395553/) onto your computer. Ledger Live is the app you use to manage your Ledger device.  Please follow the official installation instruction [here](https://support.ledger.com/hc/en-us/articles/360006395553). 
2. [Install the latest firmware](https://support.ledgerwallet.com/hc/en-us/articles/360002731113) on your Nano S. This ensures compatibility with the Harmony app. The latest firmware is version 1.6.0 .   

{% embed url="https://youtu.be/\_5CymmI4BTQ" %}

At this point, you're ready to install apps on your Ledger Nano S. Remember to store your 24-word recovery phrase in a safe place, because you'll need it to recover your funds if your device is lost or damaged.

## Install Ledger Nano S Firmware In Debugging Mode

_This is ONLY for wallet developers / testers._ 

1. Download Ledger firmware from [here](https://s3-us-west-1.amazonaws.com/pub.harmony.one/release/ledger_firmware/ver1_app.hex) .
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
sudo ./venv/bin/python -m ledgerblue.loadApp --appFlags 0x40 --path "44'/1023'"  --curve secp256k1 --tlv --targetId 0x31100004 --delete --fileName ver1_app.hex  --appName One --appVersion 0.0.1 --dataSize 0 --icon 01ffffff00ffffff00ffffffffffffc7e1bbcdbbddbbcdbbc50bd8a3ddbbddbbddb3edc7e3ffffffff
```

During this process,  you will see some warning messages displayed. Read through them by pressing right button until you reach the page "Perform Installation". Press both the left and right button to confirm installation.   The Harmony Ledger App will then be installed to Ledger Nano S.

On the Ledger Nano S LCD screen, there will be a new icon for Harmony App : One.  To open the Harmony app, please click both the left and right button on top of the Ledger Nano S. A series will messages will be displayed including "This app is not genune" \(as it is a developer edition, not formal app from Ledger Live\).  Click the right button until you see "Open Application",  then click both left and right button to open the Harmony app. 

![](../../.gitbook/assets/image%20%2818%29.png)

![](../../.gitbook/assets/image%20%288%29.png)

![](../../.gitbook/assets/image%20%2820%29.png)

Once the application is opened, it will show "Waiting for commands..." in the LCD screen. This means Ledger Nano S is ready for accept commands and sign transactions from the host.

![](../../.gitbook/assets/image%20%286%29.png)

## Functionality of Harmony Ledger Nano S App

There are three major functions provided by Ledger Nano S Harmony App:

* Display the Harmony ONE address of the Ledger Nano S hardware wallet
* Sign a token transfer request using Ledger Nano S 
* Sign a staking request using Ledger Nano S

The detailed instructions for these functions are shown below.

## Display the Harmony ONE address for Ledger Nano S

![](../../.gitbook/assets/image%20%2810%29.png)

There are two buttons on top of Ledger Nano, click the right one to continue \(or click the left one to cancel\). After that, the following address will be shown on Ledger Nano S LED screen:‌

![](../../.gitbook/assets/image%20%283%29.png)

As the address is longer than the LED screen, you can use the top two button to shift the address display to the left or side right side. **Click both buttons to confirm the address.** 

The entire process is shown in video below:

{% embed url="https://youtu.be/m5RLYGWosuk" %}

