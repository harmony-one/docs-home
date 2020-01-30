# For Mac and Linux Users

{% hint style="warning" %}
_This section is only for advanced users who want to do manual installation of Harmony One app.  Please skip this section if you can install Harmony One app through Ledger Live._
{% endhint %}

## Install Ledger Nano S Firmware In Debugging Mode _****_ 

_Mac running macOS, Linux system or a Virtual Machine with USB pass through capabilities_

{% hint style="warning" %}
_To perform the testing of your Ledger Nano S with One tokens you need a Mac running macOS, a physical Linux system or a Virtual Machine with USB passthrough capabilities. The Ledger Nano S will be attached via USB to your system to test the token transfers._
{% endhint %}

* Download Ledger firmware from [here](https://s3-us-west-1.amazonaws.com/pub.harmony.one/release/ledger_firmware/ver3_app.hex) 
* Place the downloaded firmware file _**ver3\_app.hex**_ in the current working directory

#### To download using the terminal/shell:

```text
cd <working-directory>
curl https://s3-us-west-1.amazonaws.com/pub.harmony.one/release/ledger_firmware/ver3_app.hex -o ver3_app.hex
```

* Install dependencies:

#### Ubuntu/Debian distribution

```text
sudo apt install libudev1 libudev-dev libusb-1.0-0dev python3-dev python3-pip
pip3 install -U setuptools
pip3 install virtualenv
```

#### MacOS

```text
brew install python3
python3 -m pip install -U setuptools
python3 -m pip install virtualenv
```

* Set up the python loader

```text
virtualenv -p python3 venv
source venv/bin/activate
pip install ledgerblue
    (OR)
pip install git+https://github.com/LedgerHQ/blue-loader-python.git
```

* Run the following command to load the firmware to Ledger Nano S.

```text
sudo ./venv/bin/python -m ledgerblue.loadApp --appFlags 0x40 --path "44'/1023'"  --curve secp256k1 --tlv --targetId 0x31100004 --delete --fileName ver3_app.hex  --appName One --appVersion 0.0.1 --dataSize 0 --icon 01ffffff00ffffff00ffffffffffffc7e1bbcdbbddbbcdbbc50bd8a3ddbbddbbddb3edc7e3ffffffff
```

* Now, take a look at your ledger nano S, you need to enter your pin
* Choose the option to allow unsafe manager
* Install app ONE, clicking the right button until the install option appears
* Enter your password

Congratulations, step 1 is complete!

## Step 2

On the Ledger Nano S LCD screen, there will be a new icon for Harmony App : One

1. To open the Harmony app, please click both the left and right button on top of the Ledger Nano S. 
2. A series messages will be displayed including "This app is not genuine" \(as it is a developer edition, not a formal app from Ledger Live\)
3. Click the right button until you see "Open Application",  then click both left and right button to open the Harmony appOnce the application is opened, it will show "Waiting for commands..." in the LCD screen. This means Ledger Nano S is ready for accept commands and sign transactions from the host.

## Removing developer One app from your Ledger device

Since it's possible now to load a One app on the Ledger Nano S via Ledger Live \([Install Harmony One App using Ledger Live](../install-harmony-one-app-using-ledger-live.md)\) you will possibly want to delete the manually installed One app from your Ledger.

Make sure you use the following commands:

```text
virtualenv -p python3 venv
source venv/bin/activate
sudo venv/bin/python -m ledgerblue.deleteApp  --appName One  --targetId 0x31100004
```

Now check your Ledger device and approve the removal of the One app.  
And you are now ready to follow the Ledger Live installation for the One app.

