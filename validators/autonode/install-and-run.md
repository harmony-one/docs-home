---
description: Quick start to running a Harmony Validator.
---

# Install & Run

### **Step 1:** Spin up your instance on [AWS](../cloud-guides/aws.md) or [other providers](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides).

> It is recommended to go with Ubuntu 18+ or Red Hat Enterprise Linux 8+ as your operating system.

### **Step 2:** SSH into the machine.

### \(Optional\) Step 2.5: Create a user for AutoNode

You can choose any username you want. It will ask for a password and a password confirmation. We will also add this user to the `sudo` group. Please keep track of this password for future use!

```text
sudo useradd -m <your username>
sudo passwd <your username>
sudo adduser <your username> sudo
```

Now login with the new username you just created.

```text
su - <your username>
```

> Note that everytime you SSH into your machine, you can swap to your user with the command above.

### **Step 3:** Install AutoNode.

```bash
install_file_source="https://raw.githubusercontent.com/harmony-one/auto-node/mainnet-pt2/scripts/first-install.sh"
tmp_install_file="/tmp/autonode-first-install.sh"
curl -o "$tmp_install_file" "$install_file_source" && bash "$tmp_install_file" && rm -f "$tmp_install_file"
```

> Make sure to answer the prompts!

{% hint style="warning" %}
You will need to have access to `systemd` in user mode. This may require upgrading `systemd` or choosing another Operating System from your cloud provider. Ubuntu 18+ is known to work. 
{% endhint %}

### \(Optional\) Step 3.5: Update your shell.

You can reload your shell by exiting your SSH session and SSH-ing back into the machine, or you can execute the following command:

```bash
export export PATH=$PATH:~/bin
```

> This step is only needed if the command: `auto-node` does not work.

### **Step 4:** Add or import a validator key.

{% tabs %}
{% tab title="New Key" %}
```bash
auto-node hmy keys add example-validator-wallet-name
```

This is the recommended way to run AutoNode. 

You can send 10,100 ONE from your 'main' wallet to your AutoNode validator wallet \(generated with the above command\). This way, AutoNode can automate common validator commands for this new wallet, like create the validator for you. Once AutoNode creates the validator, you can delegate from your 'main' wallet to your AutoNode validator to increase its stake. 
{% endtab %}

{% tab title="Import Keystore File" %}
```
auto-node hmy keys import-ks <path-to-keystore-file>
```

Note that you can transfer files to your remote machine with the `scp` command. Documetation to do so can be found [here](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/).
{% endtab %}

{% tab title="Import Private Key \(not recommended\)" %}
```
auto-node hmy keys import-private-key <private-key-string>
```

**BE CAREFULL WITH RAW WALLET PRIVATE KEYS!!!**
{% endtab %}
{% endtabs %}

{% hint style="success" %}
You can use the following command to list all of the loaded wallets: 

```bash
auto-node hmy keys list
```
{% endhint %}

### **Step 5: Run AutoNode & start your validator!** 

```text
auto-node run --clean --fast-sync
```

> If you are curious, `--clean` is the option to ensure old node files are removed \(if present\). The `--fast-sync`option will [rclone](https://rclone.org/) the correct Harmony DB to reduce sync time. One can choose to sync from scratch by removing the `--fast-sync` option.

{% hint style="info" %}
Make sure to **respond** to the **prompts**. If you are unable to create a validator \(but started your node\) don't worry! Follow the next step on how to create your validator.
{% endhint %}

{% hint style="success" %}
One the monitor has started and you see repeated prints of the node information & headers, you can exit with `ctrl+C.`From here, you are free to do whatever on the machine, or you can exit the machine. Your Harmony node will keep running!
{% endhint %}

### **\(Optional\) Step 5.5: Create your validator after the initial Run.**

You can go through the create validator logic by executing the following command:

```text
auto-node create-validator
```

