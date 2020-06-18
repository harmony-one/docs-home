# Validator, BLS key, Instance

### Validator Setup and Configuration

A validator in Harmony blockchain is a single person or entity who stakes tokens and runs nodes \(validator client software\) to validate blocks. A validator can specify one or multiple validating keys \(a.k.a. [BLS](https://en.wikipedia.org/wiki/Boneh%E2%80%93Lynn%E2%80%93Shacham) keys\) which will be used to sign on validated blocks.

To become a validator in Harmony, you will need to do the following:

1. Setup a validator node\(s\) and let it fully synchronized with the latest blockchain. 
2. Create an on-chain validator record by sending a **CreateValidator** _****_transaction. 
3. Start validating using the node\(s\) with the BLS key\(s\) you added in your validator record

There are many fields to configure for your validator. It’s worth clarifying some of the important fields in more detail:

1. **amount:** The amount of ONE tokens the validator will stake initially.
2. **rate:** The commission fee \(%\) the validator charges from the block reward. 
3. **bls-pubkeys:** One or multiple BLS public keys the validator will sign with. Each BLS key will be used separately to bid for a slot and if successful, the key is obligated to validate blocks. 

### BLS key\(s\)

{% hint style="info" %}
[BLS](https://en.wikipedia.org/wiki/Boneh%E2%80%93Lynn%E2%80%93Shacham) stands for **Boneh–Lynn–Shacham**. It is a digital signature method used for verifying the authenticity of digital messages or documents. 
{% endhint %}

A BLS key represents what the validator signs the blocks with, and is a way of authenticating the validator. A validator can have multiple keys to sign with, this means that a validator is signing blocks in parallel.

BLS keys are attached to validator via:

* Creating a new validator \(put commas between multiple BLS keys\)
* Adding new keys to an existing validator \(edit-validator --add-bls-key\), only one key can be added at a time

### Instance\(s\) & Multi-BLS keys

An instance is a virtual private server or dedicated hardware with a unique IP address on which a validator runs the node software. 

Within each instance, there could be up to 4 BLS keys signing transactions. If you have more than a single BLS key in your instance, it means that you're using the **multiBLS feature**. If you have a single BLS key in the instance, we will call that single-key instance.

Here are **some rules to follow:**

* In order to use multiBLS feature \(multiple BLS keys in same instance\), all keys are required to be on the **same shard**
* Total number of BLS keys allowed per validator is **1/3 of total external seats** \(network level\)

Note that validators sometimes choose to run duplicate instances \(2 instances, each running with same BLS key\) as a backup mechanism.

Below are some differences to using multiBLS vs. single-key instance:

* Machine cost will be lower in a multiBLS instance \(compare 'validator 2' vs. 'validator 1'\)
* Single-key instances could run nodes for a validator in different shards, whereas a multiBLS instance requires all BLS keys to be in the same shard
* MultiBLS and single-key instance have different staking commands
* In order to make changes to the keys in a multiBLS instance, the node needs to be stopped and restarted; whereas a single-key instance can be directly added to a validator \(since the node is running on a different instance\)
* Too many BLS keys signing using a single node creates a single point of failure \(validator’s risk\)

### Visualization

![](../../../.gitbook/assets/image%20%28101%29.png)

![](../../../.gitbook/assets/image%20%2871%29.png)

