---
description: Run the latest AutoNode!
---

# Update

## Checking for AutoNode updates

AutoNode will quickly check for an update on each execution of the `auto-node` command. If there is an update you will see the following message:

![](../../../../../.gitbook/assets/image%20%28192%29.png)

## Updating AutoNode

{% hint style="warning" %}
You will need to briefly stop your node to execute an update. Updates should be fast.
{% endhint %}

### Step 0: \(Optional\) Stop Auto 

Kill your AutoNode with the following command:

```text
auto-node kill
```

> Note that if you are still elected and signing, AutoNode will ask for you to confirm before killing your node.

### Step 1: Start the update

You can start the update with the following command:

```text
auto-node update
```

> Note that AutoNode will check to make sure the harmony node is stopped. If it detects that the harmony node is still running, It will ask to kill itself before starting the update.

{% hint style="success" %}
You can also re-run the install script from step 3 of the **Install & Run** script to update AutoNode
{% endhint %}

### Step 2: Restart/Rerun your AutoNode

Make sure to restart your AutoNode after the update to resume validating or operations.  
For a validator, it will most likely be:

```text
auto-node run
```

> **DO NOT** restart AutoNode with the `--clean` or `--fast-sync` as it will probably regress your block hight \(since it edits the DB files\).

## Updating `hmy` CLI

For your convenience, AutoNode wraps the `hmy` [CLI. ](https://docs.harmony.one/home/wallets/harmony-cli)You can update it with the following command:

```text
auto-node hmy-update
```

