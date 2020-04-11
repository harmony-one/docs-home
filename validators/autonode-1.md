---
description: >-
  AutoNode allows you to spin up a node seamlessly. It will automatically make
  sure your validator is active and signing as well as refresh your node on hard
  resets.
---

# AutoNode

## 1. Install Docker & Tmux

**Step 1:** Spin up your instance on [AWS](first-time-setup/cloud-guides/aws.md) or [other providers](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides).

> It is recommended to go with Ubuntu or Amazon Linux as your operating system.

**Step 2:** [SSH](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws#step-2-connecting-to-your-aws-instance) into the machine.

**Step 3:** Setup the machine \(Docker\):

{% tabs %}
{% tab title="Ubuntu" %}
```bash
sudo apt-get update -y && sudo apt install docker.io -y \
&& sudo usermod -aG docker $USER && sudo systemctl start docker \
&& sudo systemctl enable docker && sudo apt install tmux -y \
&& exit
```
{% endtab %}

{% tab title="Amazon Linux" %}
```bash
sudo yum update -y && sudo yum install -y docker \
&& sudo usermod -aG docker $USER && sudo service docker start \
&& sudo yum install -y tmux \
&& exit
```
{% endtab %}
{% endtabs %}

> For more details on how to setup docker, reference [this](https://docs.docker.com/engine/install/).

{% hint style="info" %}
The above command with exit out of SSH for you \(needed for docker install\). SSH back into the machine.
{% endhint %}

## 2. Configure Validator

**Step 1:** Download the Harmony CLI:

```bash
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

**Step 2:** Create a new key or import an existing key:

{% tabs %}
{% tab title="New Key" %}
```bash
./hmy keys add validator
```
{% endtab %}

{% tab title="Import Key" %}
```bash
./hmy keys import-private-key <private-key>
```
{% endtab %}
{% endtabs %}

**Step 3:** Download latest `auto_node.sh` version:

```bash
curl -O https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/auto_node.sh \
&& chmod +x ./auto_node.sh
```

**Step 4**: Setup `auto_node.sh`:

```bash
./auto_node.sh setup
```

**Step 5:** Edit the `validator_config.json` file:

{% tabs %}
{% tab title="Edit Command" %}
```bash
nano validator_config.json
```
{% endtab %}

{% tab title="Example File" %}
```bash
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
    "max-total-delegation": 100000000.0,
    "details": "None"
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Note that the ONE address has to be in quotes
{% endhint %}

**Step 6:** Save and exit config by pressing **Ctrl + O** then hit enter, then press **Ctrl + X**:

{% hint style="info" %}
Optional: fund the account. If faucet is working, auto node will automatically fund the account if needed.
{% endhint %}

## **3. Run AutoNode**

**Step 1:** Open a new tmux session by running the command bellow. "Node" will be the name of your tmux session:

```bash
tmux new-session -s node
```

{% hint style="info" %}
In case you already have a tmux session named "node" running you can just attach it by running:`tmux attach-session -t node`
{% endhint %}

**Step 2:** Run the node:

{% hint style="info" %}
Make sure you have the latest AutoNode version installed before running it. To download the latest version proceed to[ Section 3](https://docs.harmony.one/home/validators/autonode-1#2-configure-validator) and execute Step 3.
{% endhint %}

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
./auto_node.sh export-bls . && mkdir -p harmony_bls_keys \
&& cp -R bls_keys/. harmony_bls_keys/
```

This ensures that the BLS key will be reused should you have to relaunch your node.
{% endhint %}

{% hint style="info" %}
Optional: once detached, export the node information with `./auto_node.sh export`
{% endhint %}

