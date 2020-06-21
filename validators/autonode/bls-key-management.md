---
description: Manage and re-use your BLS keys.
---

# BLS key management

### BLS key\(s\) location

You can find the path to your BLS keys directory with the following command:

```bash
python3 -c "from AutoNode import common; print(common.bls_key_dir)"
```

> By default, this should be `~/.hmy/blskeys`

{% hint style="warning" %}
Any BLS key **present** in that directory will be attempted to be used when launching the node. This means that all BLS keys in the said directory **need** to be for the **same** **shard**. Moreover, any `.pass`files will also be attempted to be used when launching a node
{% endhint %}

### BLS key for shard

{% hint style="info" %}
This assumes AutoNode has been initialized.
{% endhint %}

You can find which shard a public BLS key belongs to with the following command:

```bash
auto-node bls-shard <public-bls-key>
```

### Cleanse BLS key\(s\) from Validator

You can automatically cleanse your validator of BLS key\(s\) that have not signed any blocks in the current epoch with the following command:

```bash
auto-node cleanse-bls
```

You can cleanse all BLS key\(s\) that are not on the same shard as the BLS key\(s\) used by the current harmony node's shard with the following command:

```bash
auto-node cleanse-bls --keep-shard
```

You can also cleanse the BLS key\(s\) that are not being used by the current harmony node with the following command:

```bash
auto-node cleanse-bls --hard
```

### Remove BLS key from Validator

You can remove an explicit BLS key from your validator with the following command:

```bash
auto-node remove-bls <public-bls-key>
```

