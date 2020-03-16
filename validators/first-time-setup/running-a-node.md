---
description: Using node.sh
---

# Running a Node

## Download node.sh

**1.** Run the following command to download the node.sh script:

```text
curl -LO https://raw.githubusercontent.com/harmony-one/harmony/master/scripts/node.sh && chmod a+x node.sh
```

## TMUX

Install tmux if your Linux distribution does not already come with it. 

```text
sudo yum install tmux
```

## Run Node

**1.** Create a new tmux session called "node".

```text
tmux new-session -s node
```

{% hint style="info" %}
You'll want to use a tmux session in order to leave your node running, while you are not connected to your instance.
{% endhint %}

{% hint style="danger" %}
For any Debian based OS like Ubuntu and others, please install the package below in case you are NOT running statically linked binaries via parameter `-I`:

```text
sudo apt-get install libgmp-dev
```
{% endhint %}

**2.** Run the node.sh script with the following command. Once you do, it will ask for a passphrase for your BLS key file. Type your passphrase on the screen that follows and your node should be up and running.

{% tabs %}
{% tab title="Open Staking Network" %}
```
./node.sh -S -c -z -I -N staking -k [BLS KEY FILE].key
```
{% endtab %}

{% tab title="Partner Network" %}
```text
./node.sh -S -c -z -I -N partner -k [BLS KEY FILE].key
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Use `-S` to run node.sh as any user.

Use `-c` to automatically clear old data for a refreshed network.

Use `-z` to run with staking enabled.

Use `-I` to run with the statically linked binary \(recommended\).

Use `-N [NETWORK]` to specify which network to connect to.

Use `-k [BLS KEY FILE]` to specify which BLS key to run the node with.
{% endhint %}

{% hint style="danger" %}
Only use `-c` for our testing networks. Do not use for Mainnet.
{% endhint %}

**3.** Detach your "node" tmux session by press \[**Ctrl\]+b**, releasing and and then press **d**. Detaching from your session will allow you to safely disconnect from your instance, while leaving your node running in the cloud.

**4.** To check if your node is syncing properly, run the below command and check that the block height is greater than 0.

```text
./hmy blockchain latest-header
```

## Multiple BLS Keys \(Optional\)

Optionally, you can run the node using multiple BLS keys if you want. 

**1.** Keys are loaded from `.hmy/blskeys` folder which has to be created first:

```text
mkdir -p .hmy/blskeys
```

**2.** Copy all the [previously created BLS key\(s\)](https://docs.harmony.one/home/validators/first-time-setup/generating-a-bls-key) to this new folder:

```text
cp *.key .hmy/blskeys
```

{% hint style="warning" %}
Make sure all your BLS keys belong to the same shard when using multiple BLS keys. You can use the command below to check each one of them.
{% endhint %}

{% tabs %}
{% tab title="Open Staking Network" %}
```
./hmy --node=https://api.s0.os.hmny.io utility shard-for-bls [BLS PUBLIC KEY]
```
{% endtab %}

{% tab title="Partner Network" %}
```text
./hmy --node=https://api.s0.ps.hmny.io utility shard-for-bls [BLS PUBLIC KEY]
```
{% endtab %}
{% endtabs %}

**3.** For each BLS key file, a corresponding `<blskey>.pass` file needs to be created inside folder`.hmy/blskeys`with the passphrase inside it.

{% hint style="warning" %}
For any `.key` if no passphrase file is available, it will use the default specified when running the node e.g., `./node.sh -p blspass.txt`
{% endhint %}

**4.** You can now run the node using parameter **-M** for multiple BLS keys. Parameter **-k** will not be used anymore as we are loading multiple BLS keys here:

```text
./node.sh -S -c -z -I -N staking -M
```

## Helpful Information

To re-attach to your tmux session where your `node.sh` is running, use the following command:

```text
tmux attach-session -t node
```

[TMUX Cheatsheet](https://gist.github.com/henrik/1967800)

