---
description: >-
  AutoNode allows you to spin up a node seamlessly. It will automatically make
  sure your validator is active and signing as well as refresh your node on hard
  resets.
---

# AutoNode without Docker

**Step 1:** Spin up your instance on [AWS](first-time-setup/cloud-guides/aws.md) or [other providers](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides).

> It is recommended to go with Ubuntu or Amazon Linux as your operating system.

**Step 2:** [SSH](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws#step-2-connecting-to-your-aws-instance) into the machine.

**Step 3:** Install dependencies: \(python3-pip, jq\)

{% tabs %}
{% tab title="Amazon Linux" %}
```bash
sudo yum update && sudo yum install python3-pip jq -y
```
{% endtab %}
{% endtabs %}

**Step 4:** Install AutoNode

{% tabs %}
{% tab title="Amazon Linux" %}
```bash
bash <(curl -s -S -L https://raw.githubusercontent.com/harmony-one/auto-node/migrate_off_docker/scripts/install.sh)
```
{% endtab %}
{% endtabs %}

**Step 5:** Add or import validator Key

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

**Step 5:** Edit the config

{% tabs %}
{% tab title="Edit Command" %}
```bash
nano validator_config.json
```
{% endtab %}

{% tab title="Example" %}
```
{
    "validator-addr": "YOUR ONE1 ADDRESS",
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

**Step 6:** Save and exit config by pressing **Ctrl + X** then **Y**, then hit **enter**.

**Step 7:** Fund your one1 account. For OSTN, the faucet is [here](https://faucet.os.hmny.io/).

**Step 8:** Run your validator

{% tabs %}
{% tab title="Amazon Linux" %}
```bash
./auto_node.sh run --auto-active --auto-reset --clean
```
{% endtab %}
{% endtabs %}

Answer the prompts with `Y` or `N` \(this process may take a minute\)

Once you see a loop of the node's header information \(labeled something like `This node's latest header at 2020-04-11 05:35:06.065816: { ...`\), feel free to exit with **Ctrl+Z**

And that's it, you're done! Feel free to exit the SSH session. 

**Step 9:** Monitor your node

{% tabs %}
{% tab title="Amazon Linux" %}
```bash
./auto_node.sh status
```
{% endtab %}
{% endtabs %}

feel free to exit with Ctrl+Z

