---
description: >-
  AutoNode allows you to spin up a node seamlessly. It will automatically make
  sure your validator is active and signing as well as refresh your node on hard
  resets.
---

# AutoNode

## **Installing AutoNode**

### **Step 1:** Spin up your instance on [AWS](cloud-guides/aws.md) or [other providers](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides).

> It is recommended to go with Ubuntu or Amazon Linux as your operating system.

### **Step 2:** [SSH](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws#step-2-connecting-to-your-aws-instance) into the machine.

{% hint style="warning" %}
AutoNode **DOES NOT** run with root, thus you need to login with a user that is not root. 

**Most cloud providers \(like AWS\) give you such an account as the default login.** However, if you don't have a user that is not root, follow the procedures below to create one, otherwise you can just skip this part and go to Step 3.
{% endhint %}

You can choose any username you want. It will ask for a password and a password confirmation. We will also add this user to the sudo group. Please keep track of this password for future use!

```text
sudo useradd -m <your username>
sudo passwd <your username>
sudo adduser <your username> sudo
```

Now login with the new username you just created.

```text
su - <your username>
```

{% hint style="warning" %}
If you wish to automatically reset your node during hard resets \(the `--auto-reset` option in step 7\) your user \(`<your username>`\)  must have sudo access without a passphrase. Follow instructions [here](https://www.cyberciti.biz/faq/linux-unix-running-sudo-command-without-a-password/) to set that up. 

If you don't want to do that, you can still run AutoNode! Only thing is that on hard resets, you have to do is step 6 and 7 to restart your node.
{% endhint %}

### **Step 3:** Install AutoNode.

```bash
curl -O https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/install.sh && chmod +x ./install.sh && ./install.sh && rm ./install.sh
```

{% hint style="info" %}
If you are upgrading your AutoNode from a previous version the installer might ask you some questions. Answer with Y for the upgrading process to go on.
{% endhint %}

### **Step 4:** Add or import a validator key.

{% tabs %}
{% tab title="New Key" %}
```bash
./hmy keys add validator
```
{% endtab %}

{% tab title="Import Keystore File" %}
```
./hmy keys import-ks <path-to-keystore-file>
```
{% endtab %}

{% tab title="Import Private Key \(not recommended\)" %}
```
./hmy keys import-private-key <private-key-string>
```
{% endtab %}
{% endtabs %}

### **Step 5:** Edit the configuration file and change the `validator-addr`to the ONE address created on Step 4. 

```text
./auto_node.sh edit-config
```

> Note that `identity` must be unique or else your validator won't get created.

> Save and exit the configuration by pressing **Ctrl + X** then **Y**, then by hitting **enter**.

{% hint style="warning" %}
Note that the ONE address has to be in quotes
{% endhint %}

### **Step 6: Fund your ONE address.**

### **Step 7 :** Run your validator.

```text
./auto_node.sh run --auto-active --auto-reset --clean
```

> Answer the prompts with `Y` or `N` \(this process may take a minute\).   
> Feel free to exit with **Ctrl+Z** after your node syncs!

{% hint style="info" %}
You can view all the commands for AutoNode with `~/auto_node.sh -h`
{% endhint %}

## **Monitoring**

{% hint style="success" %}
If any of the commands activates a monitoring screen,  you can always exit using **Ctrl**+**Z**.
{% endhint %}

### **1\) View the log of your Harmony Monitor:**

```text
./auto_node.sh monitor log
```

### 2\) Using TUI

```text
./auto_node.sh tui run
```

![](../.gitbook/assets/image%20%2881%29.png)

### 3\) View the status of your Harmony Monitor daemon:

```text
./auto_node.sh monitor status
```

### 4\) Restart your Harmony Monitor daemon:

```text
./auto_node.sh monitor restart
```

## Upgrade AutoNode

### 1\) Deactivate your validator during the upgrade process

```text
./auto_node.sh deactivate
```

### 2\) Safely kill AutoNode & its monitor \(if alive\)

```text
 ./auto_node.sh kill
```

### 3\) Update AutoNode by running the install step again:

```bash
curl -O https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/install.sh && chmod +x ./install.sh && ./install.sh && rm ./install.sh
```

### 4\) Start up your node again but this time _without_ the `--clean` option.

```text
 ./auto_node.sh run --auto-active --auto-reset
```

> Once your node is done syncing, AutoNode will automatically activate your validator to be elected in the next epoch!

### 5\) \(Optional\) If needed, you might have to activate your validator manually, do so with:

```text
./auto_node.sh activate
```

## Cleaning Keys

### 1\) You can cleanse your BLS \(based on performance of a key\) with:

```text
 ./auto_node.sh cleanse-bls
```

### 2\) Remove all keys except for keys running on your current autonode with:

```text
./auto_node.sh cleanse-bls --hard
```

## More detailed documentation can be found [here](https://github.com/harmony-one/auto-node).

> Feel free to contribute or open issues!

