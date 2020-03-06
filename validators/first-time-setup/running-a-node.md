---
description: Using node.sh
---

# Running a Node

## Download node.sh

**1.** Run the following command to download the node.sh script:

```text
curl -LO https://harmony.one/node2.sh && mv node2.sh node.sh && chmod a+x node.sh
```

{% hint style="warning" %}
Node2.sh is a temporary script just for the Open Staking Testnet.
{% endhint %}

## Run Node

**1.** Create a new tmux session called "node".

```text
tmux new-session -s node
```

{% hint style="info" %}
You'll want to use a tmux session in order to leave your node running, while you are not connected to your instance.
{% endhint %}

{% hint style="danger" %}
If you want to run a node on Ubuntu, also run the following commands to get the required libraries:

```text
curl -LO http://pub.harmony.one.s3.amazonaws.com/release/linux-x86_64/testnet/libcrypto.so.10
sudo apt-get install libgmp-dev
```
{% endhint %}

**2.**  Run the node.sh script with the following command. Once you do, it will ask for a passphrase for your BLS key file. Type your passphrase on the screen that follows and your node should be up and running.

```css
./node.sh -S -N staking -z -k [BLS KEY FILE].key
```

{% hint style="info" %}
Use `-S` to run node.sh as any user.

Use `-z` to run with staking enabled.

Use `-N [NETWORK]` to specify which network to connect to.

Use `-k [BLS KEY FILE]` to specify which BLS key to run the node with.
{% endhint %}

**3.** Detach your "node" tmux session by press \[**Ctrl\]+b**, releasing and and then press **d**. Detaching from your session will allow you to safely disconnect from your instance, while leaving your node running in the cloud.

**4.** To check if your node is syncing properly, run the below command and check that the block height is greater than 0.

```text
./hmy blockchain latest-header
```

## Helpful Information

To re-attach to your tmux session where your `node.sh` is running, use the following command:

```text
tmux attach-session -t node
```

[TMUX Cheatsheet](https://gist.github.com/henrik/1967800)

