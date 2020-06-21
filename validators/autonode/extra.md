---
description: Some optional extras that you may find useful.
---

# Extra

{% hint style="info" %}
All commands for `auto-node` have a help message that describes its usage. Just append `--help` to the command you wish to learn more about. For example: `auto-node --help.`
{% endhint %}

## Running AutoNode on Testnet

By default, AutoNode will be set-up to run on Mainnet, without any additional options needed.   
However, it is easy to make AutoNode run on Testnets! To run AutoNode on the main Harmony Testnet, you just have to execute the run command with 2 extra options, the **network** name, and **beacon-endpoint** \(aka shard 0 endpoint\). So your run command for Testnet may look like this:

```text
auto-node run --clean --fast-sync --expose-rpc \ 
    --network testnet --beacon-endpoint https://api.s0.b.hmny.io/
```

## Run your node in Archival mode

AutoNode can run nodes in archival nodes if you wish.   
**Make sure your machine has enough space.** We expect around 500GB is needed to run an Archival node.

You can run the archival node by simply adding the `--archival` option to the end of the run command. So your run command may look like this:

```text
auto-node run --clean --fast-sync --expose-rpc --archival
```

## Using wallet passphrase from file

We **do not** recommend storing your passphrase in plain text. If you choose to, you can have AutoNode import your wallets passphrase from a file. First, save the passphrase using the following convention:

```text
<ONE-address>.pass
```

Then, move the saved passphrase into the harmony wallet passphrase directory using the following command:

```text
mv ./path/to/<ONE-address>.pass ~/harmony_wallet_pass/<ONE-address>.pass
```

Then, when you run AutoNode with `auto-node run` it will automatically pick up the passphrase.

