---
description: Manage and re-use your BLS keys
---

# BLS key management

### BLS key\(s\) location

You can find the path to your BLS keys directory with the following command:

```bash
python3 -c "from AutoNode import common; print(common.bls_key_dir)"
```

{% hint style="warning" %}
Any BLS key **present** in that directory will be attempted to be used when launching the node. This means that all BLS keys in the said directory **need** to be for the **same** **shard**. Moreover, any `.pass`files will also be attempted to be used when launching a node
{% endhint %}

### BLS key for shard

{% hint style="info" %}
This assumes AutoNode has been initialized.
{% endhint %}

You can find which shard a public BLS key belongs to with the following command:

```bash
auto-node bls-shard 9024162cfebaaafcbd097156b67c9f33b8e57dd2aecde3cae55524692c9e0d60467ead669ede298a9aa8a51a1a30f787
```

### Cleanse BLS Key\(s\) from Validator

You can remove BLS key\(s\) from a Validator if a BLS key has not signed any blocks in the current epoch. Do so with the following command:

```bash
auto-node cleanse-bls
```

You can remove all BLS keys that are not for the current Nodes with the following command:

```bash
auto-node cleanse-bls --keep-shard
```

You can also remove BLS key\(s\) from a validator if they are not being used by the node program. Do so with the following command:

```bash
auto-node cleanse-bls --hard
```

  


