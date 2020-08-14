---
description: Quick start to running a Harmony Validator.
---

# Install & Run

{% hint style="info" %}
All commands for `auto-node` have a help message that describes its usage. Just append `--help` to the command you wish to learn more about. For example: `auto-node --help.`
{% endhint %}

### **Step 1:** Spin up your instance on [AWS](../../../../cloud-setup/cloud-guides/aws.md) or [other providers](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides)

> It is recommended to go with Ubuntu 18+ or Red Hat Enterprise Linux 8+ as your operating system.

### **Step 2:** SSH into the machine

### Step 2.5: \(Optional\) Create a new user

You can choose any `<new-user-name>` you want. The command below will ask for a passphrase for the user, choose one and keep track of this password for future use! The command below will also add the user to the sudo group for convenience. 

```bash
new_user_name=<new-user-name>
sudo adduser $new_user_name
```

Answer the prompts, then execute:

```bash
sudo adduser $new_user_name sudo
sudo loginctl enable-linger $new_user_name
```

Next, if you wish to use the same SSH credentials as your current user to log into your new user, execute the following commands:

```bash
sudo mkdir -p /home/$new_user_name/.ssh
sudo cp ~/.ssh/authorized_keys /home/$new_user_name/.ssh/authorized_keys
sudo chown $new_user_name:$new_user_name /home/$new_user_name/.ssh/authorized_keys
```

> Command above assumes you use the default home directory for your new user

Otherwise, you can create your own SSH key for your user following [this](https://www.cyberciti.biz/faq/how-to-set-up-ssh-keys-on-linux-unix/) documentation.

Lastly, exit your SSH session and re-SSH back into your machine under your new user. Your ssh command may look something like this:

```bash
ssh -i "key.pem" <new-user-name>@your-server.com
```

Alternatively, you can swap users when SSH-ed in as your default user with the following command:

```bash
su - <new-user-name>
```

If you choose to swap users, you must export 2 environment variables to install AutoNode. Do so with the following command:

```bash
export XDG_RUNTIME_DIR="/run/user/$UID"
export DBUS_SESSION_BUS_ADDRESS="unix:path=${XDG_RUNTIME_DIR}/bus"
```

> It may be convient to add this command to your `~/.bashrc` profile.

### **Step 3:** Install AutoNode

`sudo` access for your user is needed for installation.

```bash
install_file_source="https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/first-install.sh"
tmp_install_file="/tmp/autonode-first-install.$(date +'%s').sh"
curl -o "$tmp_install_file" "$install_file_source" && bash "$tmp_install_file" && rm -f "$tmp_install_file"
```

> Make sure to answer the prompts!

{% hint style="warning" %}
You will need to have access to `systemd` in user mode. This may require SSH-ing in as the user running AutoNode, or upgrading `systemd.` It may be easier to choose another Operating System if you have to upgrade `systemd`, Ubuntu 18+ is known to work. 

If you created a user just for AutoNode, make sure to follow all parts of step 2. 
{% endhint %}

### Step 3.5: \(Optional\) Update your shell

You can reload your shell by exiting your SSH session and SSH-ing back into the machine, or you can execute the following command:

```bash
export PATH=$PATH:~/bin
```

> This step is only needed if the command: `auto-node` does not work.

### **Step 4:** Add or import a Validator Key

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

### **Step 5: Run AutoNode & start your Validator**

{% tabs %}
{% tab title="Mainnet" %}
```bash
auto-node run --clean --fast-sync
```
{% endtab %}

{% tab title="Testnet" %}
```bash
auto-node run --clean --fast-sync --auto-active \
    --network testnet --beacon-endpoint https://api.s0.b.hmny.io/ --shard 0
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Use `--clean` to start fresh/remove old node files \(if present\)

Use `--fast-sync` option to rclone the correct Harmony DB to reduce sync time. One can choose to sync from scratch by removing the `--fast-sync` option

Use `--expose-rpc` if you wish to expose [RPC](https://en.wikipedia.org/wiki/Remote_procedure_call) for your node to enable endpoint functionality

Use `--shard` \(your shard number here\) to run a node for a specific shard

Use `--archival` to run in archival mode. Make sure your machine has enough space. We expect around 500GB is needed to run an Archival node \(Jun 2020\)

Use `--auto-active` to automatically activate your validator on next epoch in case it gets deactivated
{% endhint %}

{% hint style="warning" %}
Make sure to **respond** to the **prompts**. If you are unable to create a validator \(but started your node\) don't worry! Follow the next step on how to create your validator.
{% endhint %}

{% hint style="success" %}
Once the monitor has started and you see repeated prints of the node information & headers, you can exit with `ctrl+C.`From here, you are free to do whatever on the machine, or you can exit the machine. Your Harmony node will keep running!
{% endhint %}

### **Step 5.5: \(Optional\) Create your validator after the initial run**

You can go through the create validator flow again by executing the following command:

```text
auto-node create-validator
```

> Note that this can only be done if you failed to create a validator on the inital run of auto-node

