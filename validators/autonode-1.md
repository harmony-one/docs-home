---
description: >-
  AutoNode allows you to spin up a node seamlessly. It will automatically make
  sure your validator is active and signing as well as refresh your node on hard
  resets.
---

# AutoNode

#### Note that steps 1 - 4 are for installing _Docker_ and _Tmux_ on an AWS machine. So long as you have said things installed on ur machine of choice, the autonode will work.

> Skip to step 5 if you have a machine setup with Docker and Tmux.

**Step 1:** Spin up your instance on [AWS](first-time-setup/cloud-guides/aws.md)

> It is recommended to select the following AMI: _Amazon Linux 2 AMI \(HVM\), SSD Volume Type_

**Step 2:** [SSH](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws#step-2-connecting-to-your-aws-instance) into the machine

**Step 3:** Setup the machine \(Docker and tmux\) 

```bash
sudo yum update -y && sudo yum install -y docker && sudo usermod -aG docker ec2-user && sudo service docker start && sudo yum install -y tmux && exit
```

> For more details on how to setup docker, reference [this](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html).

**Step 4:** The above command with exit out of SSH for you \(needed for docker install\). SSH back into the machine.

**Step 5:** Download the Harmony CLI:

```bash
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

**Step 6:** Download the `auto_node.sh` shell script. All things related to the node will be done using this script.

```bash
curl -LO https://harmony.one/auto-node && mv auto-node auto_node.sh && chmod +x ./auto_node.sh && ./auto_node.sh setup
```

**Step 7:** Create a new key or import an existing key

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

**Step 8:** Edit the `validator_config.json` file

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

**Step 9:** Save and exit config by pressing **Ctrl + O** then hit enter, then press **Ctrl + X**

{% hint style="info" %}
Optional: fund the account. If faucet is working, auto node will automatically fund the account if needed.
{% endhint %}

**Step 10:** Open new tmux session with `tmux new-session -s`  

**Step 11:** Run the node

```bash
./auto_node.sh run --auto-active --auto-reset --auto-interaction --clean
```

> Answer the prompts with `Y` or `N`

{% hint style="info" %}
Detach from tmux session afterwards by pressing ctrl + b, then d 
{% endhint %}

{% hint style="info" %}
Optional: once detached, export the BLS key files with: 

```bash
rm -rf ./bls_keys && ./auto_node.sh export-bls . && mkdir harmony_bls_keys && cp -R bls_keys/. harmony_bls_keys/
```

This ensures that the BLS key will be reused should you have to relaunch your node.
{% endhint %}

{% hint style="info" %}
Optional: once detached, export the node information with `./auto_node.sh export`
{% endhint %}

