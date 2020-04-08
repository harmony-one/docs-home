---
description: >-
  AutoNode allows you to spin up a node seamlessly, and will automatically make
  sure your validator is active and signing. Note you can only run one bls key
  on AutoNode.
---

# AutoNode

#### Step 1: Spin up your instance on [AWS](first-time-setup/cloud-guides/aws.md)

#### Step 2: [SSH](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws#step-2-connecting-to-your-aws-instance) into the machine

#### Step 3: Setup the machine \(install CLI, Docker, and tmux\) 

```text
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy && sudo yum update -y && sudo yum install -y docker && sudo usermod -aG docker ec2-user && sudo service docker start && sudo yum install -y tmux && exit
```

#### Step 4: The above command with exit out of SSH for u \(needed for docker install\). SSH back into the machine

#### Step 5: Download the auto\_node shell script

```text
curl -O https://raw.githubusercontent.com/harmony-one/harmony-ops/master/devops/auto_node/scripts/auto_node.sh && chmod +x ./auto_node.sh && ./auto_node.sh setup
```

#### Step 6: Create new key or import key 

{% tabs %}
{% tab title="New Key" %}
```text
./hmy keys add validator
```
{% endtab %}

{% tab title="Import Key" %}
```
./hmy keys import-private-key <private-key>
```
{% endtab %}
{% endtabs %}

#### Step 7: Edit the create-validator config

{% tabs %}
{% tab title="Config" %}
```text
nano validator_config.json
```
{% endtab %}

{% tab title="Example" %}
```
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

{% hint style="info" %}
The one address has to be in quotes
{% endhint %}

#### Step 8: Save and exit config by pressing ctrl + O then hit enter, then press ctrl + X

{% hint style="info" %}
Optional: fund the account. If faucet is working, auto node will automatically fund the account if needed.
{% endhint %}

#### Step 9: Open new tmux session with `tmux new-session -s`  

#### Step 10: Run node

```text
./auto_node.sh run --shard 1 --auto-active --auto-interaction --clean
```

{% hint style="info" %}
Detach from tmux session afterwards by pressing ctrl + b, then d 
{% endhint %}

{% hint style="info" %}
Optional: once detached, export the node information with `./auto_node.sh export`
{% endhint %}

## AutoNode Reset 

To reset node after network refresh, just connect to the tmux session and run: 

```text
./auto_node.sh run --shard 1 --auto-active --auto-interaction --clean
```

