---
description: Install Harmony App for Ledger Nano S & Hardware Wallet
---

# Install and Setup

## Set up your Ledger Nano S

_Let's make sure your hardware wallet ready to use._

1. [Initialize](https://support.ledgerwallet.com/hc/en-us/articles/360000613793) your Ledger Nano S. This gets the hardware wallet set up and ready to use.

{% embed url="https://youtu.be/JlojlZiVK8E" %}

1. Download [Ledger Live](https://support.ledgerwallet.com/hc/en-us/articles/360006395553/) onto your computer. Ledger Live is the app you use to manage your Ledger device.  Please follow the official installation instruction [here](https://support.ledger.com/hc/en-us/articles/360006395553). 
2. [Install the latest firmware](https://support.ledgerwallet.com/hc/en-us/articles/360002731113) on your Nano S. This ensures compatibility with the Harmony app. The latest firmware is version 1.6.0 .   

{% embed url="https://youtu.be/\_5CymmI4BTQ" %}

At this point, you're ready to install apps on your Ledger Nano S. Remember to store your 24-word recovery phrase in a safe place, because you'll need it to recover your funds if your device is lost or damaged.

_**If you are a Windows user please skip the next section until you see the windows version**_

## Install Ledger Nano S Firmware In Debugging Mode _****_ 

_Linux system or a Virtual Machine with USB pass through capabilities_

{% hint style="warning" %}
_To perform the testing of your Ledger Nano S with One tokens you need a physical Linux system or a Virtual Machine with USB passthrough capabilities. The Ledger Nano S will be attached via USB to your system to test the token transfers._
{% endhint %}

1. Download Ledger firmware from [here](https://s3-us-west-1.amazonaws.com/pub.harmony.one/release/ledger_firmware/ver3_app.hex) .
2. Place the downloaded firmware file _**ver3\_app.hex**_ in the current working directory.
3. Set up the python loader
4. **Please note**: If you run into build issues, please first try to install and run the dependencies for ledgerblue module.

```text
[sudo] pip install -U setuptools
[sudo] pip install virtualenv

#linux dependencies for ledgerblue module  
#sudo apt install libudev1 libudev-dev libusb-1.0-0-dev python3-dev

virtualenv -p python3 venv
source venv/bin/activate
pip install ledgerblue
or pip install git+https://github.com/LedgerHQ/blue-loader-python.git
```

1. Run the following command to load the firmware to Ledger Nano S.

```text
sudo ./venv/bin/python -m ledgerblue.loadApp --appFlags 0x40 --path "44'/1023'"  --curve secp256k1 --tlv --targetId 0x31100004 --delete --fileName ver3_app.hex  --appName One --appVersion 0.0.1 --dataSize 0 --icon 01ffffff00ffffff00ffffffffffffc7e1bbcdbbddbbcdbbc50bd8a3ddbbddbbddb3edc7e3ffffffff
```

-Now, take a look at your ledger nano S, you need to enter your password

-Allow unsafe manager

-Install app ONE, click right bottom until appears install

-Enter again your password

Congratulations!!

**Now scroll down this page \(ignore the windows version\) until the section "Step 2"**

## For Windows 10 Users

 You need to have the correct environment

Install Python 3.8.1 for windows, go to this website:

```
https://www.python.org/downloads/release/python-381/
```

{% hint style="info" %}
this is the latest version as 18th Jan 2019 that was tested, newer version could work or not
{% endhint %}

At the end make sure you add the python binary to the path :

![](../../.gitbook/assets/image%20%2844%29.png)

Python and pip are now installed, execute the below command on the windows terminal:

```bash
#getting the latest version of pip
python -m pip install --upgrade pip
pip install virtualenv
virtualenv venv
cd venv
cd Scripts
Activate.bat
pip install ledgerblue
```

{% hint style="info" %}
If you get an error: Running setup.py install for hidapi ... error ERROR: Command errored out with exit status 1

Go to [https://visualstudio.microsoft.com/downloads/\#build-tools-for-visual-studio-2017](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)

- Download "Build Tools For Visual Studio" under "Tools for " Visual Studio

-Launch it \(developer command Prompt for VS 2019\) and enter the the previous commands there
{% endhint %}

![](../../.gitbook/assets/image%20%281%29.png)

After the ledgerblue instalation :

1. Download Ledger firmware from [here](https://s3-us-west-1.amazonaws.com/pub.harmony.one/release/ledger_firmware/ver3_app.hex) .
2. Place the downloaded firmware file _**ver3\_app.hex**_ in the current working directory.
3. run this command:

```bash
python -m ledgerblue.loadApp --appFlags 0x40 --path "44'/1023'"  --curve secp256k1 --tlv --targetId 0x31100004 --delete --fileName ver3_app.hex  --appName One --appVersion 0.0.1 --dataSize 0 --icon 01ffffff00ffffff00ffffffffffffc7e1bbcdbbddbbcdbbc50bd8a3ddbbddbbddb3edc7e3ffffffff
```

-Now, take a look at your ledger nano S, you need to enter your password

-Allow unsafe manager

-Install app ONE, click right bottom until appears install

-Enter again your password

Congratulations!!

## Step 2

On the Ledger Nano S LCD screen, there will be a new icon for Harmony App : One. To open the Harmony app, please click both the left and right button on top of the Ledger Nano S. A series messages will be displayed including "This app is not genuine" \(as it is a developer edition, not a formal app from Ledger Live\). Click the right button until you see "Open Application",  then click both left and right button to open the Harmony app. 

![](../../.gitbook/assets/image%20%2838%29.png)

![](../../.gitbook/assets/image%20%2822%29.png)

![](../../.gitbook/assets/image%20%2841%29.png)

Once the application is opened, it will show "Waiting for commands..." in the LCD screen. This means Ledger Nano S is ready for accept commands and sign transactions from the host.

![](../../.gitbook/assets/image%20%2817%29.png)

## 

