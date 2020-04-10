---
description: >-
  AutoNode allows you to spin up a node seamlessly. It will automatically make
  sure your validator is active and signing as well as refresh your node on hard
  resets.
---

# AutoNode

#### Note that steps 1 to 6 are for installing _Docker_ and _Tmux_ on an Amazon Linux or Ubuntu. So long as you have said things installed on your machine of choice, the autonode will work.

{% hint style="success" %}
Skip to step 7 if you have a machine setup with Docker and Tmux. 
{% endhint %}

**Step 1:** Spin up your instance on [AWS](first-time-setup/cloud-guides/aws.md) or [other providers](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides).

> It is recommended to go with Ubuntu or Amazon Linux as your operating system.

**Step 2:** [SSH](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws#step-2-connecting-to-your-aws-instance) into the machine

**Step 3:** Setup the machine \(Docker\) 

{% tabs %}
{% tab title="Ubuntu" %}
```bash
sudo apt-get update -y && sudo apt install docker.io -y
```
{% endtab %}

{% tab title="Amazon Linux" %}
```bash
sudo yum update -y && sudo yum install -y docker
```
{% endtab %}
{% endtabs %}

> For more details on how to setup docker, reference [this](https://docs.docker.com/engine/install/).

**Step 4:** Check the user you are logged with using the command `who`. It will return something like the example bellow, whereas "myuser" is the user i am logging with at the moment.

```bash
who
myuser pts/0        2020-04-09 12:20 (201.48.142.117)
```

**Step 5:** Add the user returned by the command `who`to the docker group:

```bash
sudo usermod -aG docker myuser
```

**Step 6:** Enable docker, start it and install Tmux:

{% tabs %}
{% tab title="Ubuntu" %}
```bash
sudo systemctl start docker && sudo systemctl enable docker && sudo apt install tmux -y && exit
```
{% endtab %}

{% tab title="Amazon Linux" %}
```bash
sudo service docker start && sudo yum install -y tmux && exit
```
{% endtab %}
{% endtabs %}

**Step 7:** The above command with exit out of SSH for you \(needed for docker install\). SSH back into the machine.

**Step 8:** Download the Harmony CLI:

```bash
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

**Step 9:** Download the `auto_node.sh` shell script. All things related to the node will be done using this script:

```bash
curl -O https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/auto_node.sh && chmod +x ./auto_node.sh && ./auto_node.sh setup
```

**Step 10:** Create a new key or import an existing key:

{% tabs %}
{% tab title="New Key" %}
```text
./hmy keys add validator
```
{% endtab %}

{% tab title="Import Key" %}
```bash
./hmy keys import-private-key <private-key>
```
{% endtab %}
{% endtabs %}

**Step 11:** Edit the `validator_config.json` file:

{% tabs %}
{% tab title="Edit Command" %}
```bash
nano validator_config.json
```
{% endtab %}

{% tab title="Example File" %}
```javascript
{
    "validator-addr": "one1pr0xktszlvynpkf5pxft7kkwl4sauy5xcl2vsd",
    "name": "harmony_autonode",
    "website": "harmony.one",
    "security-contact": "Daniel-VDM",
    "identity": "auto-node",
    "amount": 10100,
    "min-self-delegation": 10000,
    "rate": 0.1,
    "max-rate": 0.75,
    "max-change-rate": 0.05,
    "max-total-delegation": 1000000.0,
    "details": "None"
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Note that the one address has to be in quotes
{% endhint %}

**Step 12:** Save and exit config by pressing **Ctrl + O** then hit enter, then press **Ctrl + X**:

{% hint style="info" %}
Optional: fund the account. If faucet is working, auto node will automatically fund the account if needed.
{% endhint %}

**Step 13:** Open a new tmux session by running the command bellow. "Node" will be the name of your tmux session:

```bash
tmux new-session -s node 
```

**Step 14:** Run the node:

```bash
./auto_node.sh run --auto-active --auto-reset --clean
```

> Answer the prompts with `Y` or `N`

{% hint style="info" %}
Detach from tmux session afterwards by pressing ctrl + b, then d 
{% endhint %}

{% hint style="info" %}
Optional: once detached, export the BLS key files with: 

```bash
./auto_node.sh export-bls . && mkdir -p harmony_bls_keys && cp -R bls_keys/. harmony_bls_keys/
```

This ensures that the BLS key will be reused should you have to relaunch your node.
{% endhint %}

{% hint style="info" %}
Optional: once detached, export the node information with `./auto_node.sh export`
{% endhint %}

