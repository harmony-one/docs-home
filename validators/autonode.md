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

## **Installing/Upgrading**

**Step 1:** Spin up your instance on [AWS](first-time-setup/cloud-guides/aws.md) or [other providers](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides).

> It is recommended to go with Ubuntu or Amazon Linux as your operating system.

**Step 2:** [SSH](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws#step-2-connecting-to-your-aws-instance) into the machine.

{% hint style="info" %}
AutoNode **DOES NOT** run with root, thus you need to login with a user that is not root. If you don't have a user that is not root, follow the procedures bellow to create one, otherwise you can just skip this part and go to Step 3.
{% endhint %}

{% tabs %}
{% tab title="Ubuntu LTS" %}
You can choose any username you want, it will ask for a password and a password confirmation. \(please keep track of this password for future use!\) Then we need to add this user to the sudoers group \(to give them superuser privilege\).

```text
sudo useradd -m <your username>
sudo passwd <your username>
```

Now logout of the root session \(type exit \), you should see a login as prompt, use here the username you just created.

```text
login as: <your username>
```

After giving the password you can pick up the process of install auto\_node.
{% endtab %}

{% tab title="Amazon Linux" %}
For Amazon Linux you can skip this part. Default **ec2-user** is not the **root** user.
{% endtab %}
{% endtabs %}

**Step 3:** Install AutoNode.

```text
bash <(curl -s -S -L 'https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/install.sh')
```

{% hint style="info" %}
If you are upgrading your AutoNode from a previous version the installer might ask you some questions. Answer with Y for the upgrading process to go on.
{% endhint %}

**Step 4:** Add or import a validator key.

{% tabs %}
{% tab title="New Key" %}
```bash
./hmy keys add validator
```
{% endtab %}

{% tab title="Import Key" %}
```
./hmy keys import-private-key <private-key-string>
```
{% endtab %}
{% endtabs %}

**Step 5:** Edit the configuration file and change the `validator-addr`to the ONE address created on Step 4. 

```text
./auto_node.sh edit-config
```

{% hint style="warning" %}
Note that the ONE address has to be in quotes
{% endhint %}

Save and exit the configuration by pressing **Ctrl + X** then **Y**, then by hitting **enter**.

**Step 6:** Fund your ONE account. For OSTN, the faucet is [here](https://faucet.os.hmny.io/).

**Step 7:** Run your validator.

```text
./auto_node.sh run --auto-active --auto-reset --clean
```

Answer the prompts with `Y` or `N` \(this process may take a minute\).  
Feel free to exit with **Ctrl+Z.**

## **Monitoring**

```text
1 View the log of your Harmony Monitor:

./auto_node.sh monitor log

2. View the status of your Harmony Monitor daemon:

./auto_node.sh monitor status
```

## Maintenance

```text
 1. Safely kill AutoNode & its monitor (if alive)
 
 ./auto_node.sh kill
 
 .2 Runs AutoNode with validator active 
 
 ./auto_node.sh run --auto-active
 
 3. Make validator associated with node elegable for election 
 in next epoch:
 
 ./auto_node.sh activate
 
 4. Make validator associated with node NOT elegable for election 
 in next epoch:
 
 ./auto_node.sh deactivate
```

{% hint style="info" %}
If any of the commands activates a monitoring screen,  you can always exit using **Ctrl**+**Z**.
{% endhint %}

All commands are available via help:

```text
./auto_node.sh --help
```

