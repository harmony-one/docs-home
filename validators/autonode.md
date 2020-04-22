---
description: >-
  AutoNode allows you to spin up a node seamlessly. It will automatically make
  sure your validator is active and signing as well as refresh your node on hard
  resets.
---

# AutoNode

{% hint style="info" %}
Our team is currently working on optimizing AutoNode. If you face any issues, please ask our 24/7 support group for assistance at: [https://harmony.one/volunteers](https://harmony.one/volunteers).
{% endhint %}

## **Installing AutoNode**

**Step 1:** Spin up your instance on [AWS](first-time-setup/cloud-guides/aws.md) or [other providers](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides).

> It is recommended to go with Ubuntu or Amazon Linux as your operating system.

**Step 2:** [SSH](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws#step-2-connecting-to-your-aws-instance) into the machine.

{% hint style="warning" %}
AutoNode **DOES NOT** run with root, thus you need to login with a user that is not root. 

Most cloud providers give you such an account as the default login. However, if you don't have a user that is not root, follow the procedures below to create one, otherwise you can just skip this part and go to Step 3.
{% endhint %}

{% tabs %}
{% tab title="Ubuntu LTS" %}
You can choose any username you want. It will ask for a password and a password confirmation. Please keep track of this password for future use!

```text
sudo useradd -m <your username>
sudo passwd <your username>
```

Now login with the new username you just created.

```text
su - <your username>
```
{% endtab %}

{% tab title="Amazon Linux" %}
For Amazon Linux you can skip this part. Default ec2-user is not the root user.
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
If you wish to automatically reset your node during hard resets \(the `--auto-reset` option in step 7\) your user \(`<your username>`\)  must have sudo access without a passphrase. Follow instructions [here](https://www.cyberciti.biz/faq/linux-unix-running-sudo-command-without-a-password/) to set that up. 

If you don't want to do that, you can still run AutoNode with no issues! Only thing is that on hard resets, you have to do is step 6 and 7 to restart your node.
{% endhint %}

**Step 3:** Install AutoNode.

```bash
curl -O https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/install.sh && chmod +x ./install.sh && ./install.sh && rm ./install.sh
```

{% hint style="info" %}
If you are upgrading your AutoNode from a previous version the installer might ask you some questions. Answer with Y for the upgrading process to go on.
{% endhint %}

**Step 4:** Add or import a validator key.

{% tabs %}
{% tab title="New Key" %}
```bash
~/hmy keys add validator
```
{% endtab %}

{% tab title="Import Keystore File" %}
```
~/hmy keys import-ks <path-to-keystore-file>
```
{% endtab %}

{% tab title="Import Private Key \(not recommended\)" %}
```
~/hmy keys import-private-key <private-key-string>
```
{% endtab %}
{% endtabs %}

**Step 5:** Edit the configuration file and change the `validator-addr`to the ONE address created on Step 4. 

```text
~/auto_node.sh edit-config
```

{% hint style="warning" %}
Note that the ONE address has to be in quotes
{% endhint %}

Save and exit the configuration by pressing **Ctrl + X** then **Y**, then by hitting **enter**.

**Step 6:** Fund your ONE account. For OSTN, the faucet is [here](https://faucet.os.hmny.io/).

**Step 7:** Run your validator.

```text
~/auto_node.sh run --auto-active --auto-reset --clean
```

> Answer the prompts with `Y` or `N` \(this process may take a minute\). 
>
>   
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
~/auto_node.sh monitor log
```

### 2\) View the status of your Harmony Monitor daemon:

```text
~/auto_node.sh monitor status
```

### 3\) Restart your Harmony Monitor daemon:

```text
~/auto_node.sh monitor restart
```

## Maintenance / Upgrade

### 1\) Deactivate your validator during the upgrade process

```text
~/auto_node.sh deactivate
```

### 2\) Safely kill AutoNode & its monitor \(if alive\)

```text
 ~/auto_node.sh kill
```

### 3\) Update AutoNode by running the install step again:

```bash
curl -O https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/install.sh && chmod +x ./install.sh && ./install.sh && rm ./install.sh
```

### 4\) Start up your node again but this time _without_ the `--clean` option.

```text
 ~/auto_node.sh run --auto-active --auto-reset
```

> Once your node is done syncing, AutoNode will automatically activate your validator to be elected in the next epoch

### 5\) \(Optional\) If needed, you might have to activate your validator manually, do so with:

```text
~/auto_node.sh activate
```

## More detailed documentation can be found [here](https://github.com/harmony-one/auto-node).

> Feel free to contribute or open issues!

