# For Windows Users

{% hint style="warning" %}
_his section is only for advanced users who want to do manual installation of Harmony One app.  Please skip this section if you can install Harmony One app through Ledger Live._
{% endhint %}

## Step 1

You need to have the correct environment

Install Python 3.8.1 for windows, go to this [website](https://www.python.org/downloads/release/python-381/):

{% hint style="info" %}
this is the latest version as 18th Jan 2019 that was tested, newer version could work or not
{% endhint %}

At the end make sure you add the python binary to the path :

![](../../../.gitbook/assets/image%20%2844%29.png)

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

![](../../../.gitbook/assets/image%20%281%29.png)

After the ledgerblue installation :

1. Download Ledger firmware from [here](https://s3-us-west-1.amazonaws.com/pub.harmony.one/release/ledger_firmware/ver3_app.hex)

2. Place the downloaded firmware file _**ver3\_app.hex**_ in the current working directory

3. Run this command:

```bash
$ python -m ledgerblue.loadApp --appFlags 0x40 --path "44'/1023'"  --curve secp256k1 --tlv --targetId 0x31100004 --delete --fileName ver3_app.hex  --appName One --appVersion 0.0.1 --dataSize 0 --icon 01ffffff00ffffff00ffffffffffffc7e1bbcdbbddbbcdbbc50bd8a3ddbbddbbddb3edc7e3ffffffff
```

4. Now, take a look at your ledger nano S, you need to enter your password

5. Allow unsafe manager

6. Install app ONE, click right bottom until appears install

7. Enter again your password

Congratulations, step 1 is complete!

## Step 2

On the Ledger Nano S LCD screen, there will be a new icon for Harmony App : One

1. To open the Harmony app, please click both the left and right button on top of the Ledger Nano S. 
2. A series messages will be displayed including "This app is not genuine" \(as it is a developer edition, not a formal app from Ledger Live\)
3. Click the right button until you see "Open Application",  then click both left and right button to open the Harmony appOnce the application is opened, it will show "Waiting for commands..." in the LCD screen. This means Ledger Nano S is ready for accept commands and sign transactions from the host.

## Removing developer One app from your Ledger device

Since it's possible now to load a One app on the Ledger Nano S via Ledger Live \([Install Harmony One App using Ledger Live](install-harmony-one-app-using-ledger-live.md)\) you will possibly want to delete the manually installed One app from your Ledger.

Make sure you use the following commands:

```text
cd venv
cd Scripts
Activate.bat
python -m ledgerblue.deleteApp  --appName One  --targetId 0x31100004
```

Now check your Ledger device and approve the removal of the One app.  
And you are now ready to follow the Ledger Live installation for the One app.

