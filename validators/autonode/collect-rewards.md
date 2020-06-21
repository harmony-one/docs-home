---
description: Get your ONEs for validating!
---

# Collect Rewards

### 1. Sending a Collect Rewards Transaction

You can simply collect rewards for your validator with the following command:

```bash
auto-node collect-rewards
```

### 2. \(Optional\) Send funds to your 'main' wallet

If you have followed the recommended method of creating a wallet just for running a validator, you can send funds to your 'main' wallet with the following steps.

First, get the balance of your validator wallet with the following command:

```bash
auto-node balances
```

Note the `shard 0` balance, this is where the rewards get deposited.   
Next, transfer the funds to your 'main' wallet with the following command:

```bash
auto-node balances
```

