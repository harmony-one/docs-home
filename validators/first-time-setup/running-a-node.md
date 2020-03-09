---
description: Using node.sh
---

# Running a Node

## Download node.sh

**1.** Run the following command to download the node.sh script:

{% tabs %}
{% tab title="Open Staking Network" %}
```text
curl -LO https://harmony.one/node2.sh && mv node2.sh node.sh && chmod a+x node.sh
```
{% endtab %}

{% tab title="Partner Network" %}
```text
curl -LO https://raw.githubusercontent.com/harmony-one/harmony/t3/scripts/node.sh && chmod a+x node.sh
```
{% endtab %}
{% endtabs %}

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
For any Debian based OS like Ubuntu and others, please install the package bellow as it is required to run the node:

```text
sudo apt-get install libgmp-dev
```
{% endhint %}

**2.** Run the node.sh script with the following command. Once you do, it will ask for a passphrase for your BLS key file. Type your passphrase on the screen that follows and your node should be up and running.

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

## Multiple BLS Keys \(Optional\)

Optionally, you can run the node using multiple BLS keys if you want. Keys are loaded from `.hmy/blskeys` folder which has to be created first:

```text
mkdir -p .hmy/blskeys
```

Now move all the [previously created BLS key\(s\)](https://docs.harmony.one/home/validators/first-time-setup/generating-a-bls-key) to this new folder:

```text
mv *.key .hmy/blskeys
```

{% hint style="warning" %}
Make sure all your BLS keys belong to the same shard when using multiple BLS keys. You can use the command bellow to check each one of them:
{% endhint %}

```text
./hmy utility shard-for-bls [BLS PUBLIC KEY]
```

Example with the output for a specific BLS public key:

```text
./hmy utility shard-for-bls 0f9b2407d0d54e6c7dedabce4f03bbc0e7f69c112d0a56c28ba811fe62e0f303cf4c804136da0d374273e1c52745c800
{"shard-id":0}
```

You can now run the node using parameter **-M** for multiple BLS keys. Parameter **-k** will not be used anymore as we are loading multiple BLS keys here:

```text
./node.sh -S -N staking -z -M
```

## Helpful Information

To re-attach to your tmux session where your `node.sh` is running, use the following command:

```text
tmux attach-session -t node
```

[TMUX Cheatsheet](https://gist.github.com/henrik/1967800)

