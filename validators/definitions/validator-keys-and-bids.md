# Validator, BLS key, Instance

### Validator Setup and Configuration <a id="6a31"></a>

A validator in Harmony blockchain is a single person or entity who stakes tokens and runs nodes \(validator client software\) to validate blocks. A validator can specify one or multiple validating keys \(a.k.a. [BLS](https://en.wikipedia.org/wiki/Boneh%E2%80%93Lynn%E2%80%93Shacham) keys\) which will be used to sign on validated blocks.

To become a validator in Harmony, you will need to do the following:

1. Setup a validator node\(s\) and let it fully synchronized with the latest blockchain. 
2. Create an on-chain validator record by sending a **CreateValidator** _****_transaction. 
3. Start validating using the node\(s\) with the BLS key\(s\) you added in your validator record

There are many fields to configure for your validator. It’s worth clarifying some of the important fields in more detail:

1. **amount:** The amount of ONE tokens the validator will stake initially.
2. **rate:** The commission fee \(%\) the validator charges from the block reward. 
3. **bls-pubkeys:** One or multiple BLS public keys the validator will sign with. Each BLS key will be used separately to bid for a slot and if successful, the key is obligated to validate blocks. 

For a detailed guide on how to configure your validator, please follow [**here**](https://docs.harmony.one/home/validators/managing-your-validator/changing-validator-information).

A validator technically represents a single one1.. account \(address\) that was entered into a successful create-validator transaction. Once a one1.. address is registered as a validator, the earnings of validator goes to this one1.. account.

A validator has two main parameters that affect its ranking in the committee list:

1. Stake amount
2. BLS key\(s\) attached to this validator

Validator's **bid is calculated by stake amount / \# of BLS keys**. Total stake is automatically and evenly distributed among the BLS keys, validator cannot change this.

#### BLS key\(s\)

{% hint style="info" %}
[BLS](https://en.wikipedia.org/wiki/Boneh%E2%80%93Lynn%E2%80%93Shacham) stands for **Boneh–Lynn–Shacham**. It is a digital signature method used for verifying the authenticity of digital messages or documents. 
{% endhint %}

A BLS key represents what the validator signs the blocks with, and is a way of authenticating the validator. A validator can have multiple keys to sign with, this means that a validator is signing blocks in parallel.

BLS keys are attached to validator via:

* Creating a new validator \(put commas between multiple BLS keys\)
* Adding new keys to an existing validator \(edit-validator --add-bls-key\), only one key can be added at a time

![](../../.gitbook/assets/image%20%2888%29.png)

![](../../.gitbook/assets/image%20%2862%29.png)

#### Instance\(s\)

An instance is a virtual private server or dedicated hardware with a unique IP address on which a validator runs the node software. 

Within each instance, there could be up to 4 BLS keys signing transactions. If you have more than a single BLS key in your instance, it means that you're using the **multiBLS feature**. If you have a single BLS key in the instance, we will call that single-key instance.

Here are **some rules to follow:**

* In order to use multiBLS feature \(multiple BLS keys in same instance\), all keys are required to be on the **same shard**
* Total number of BLS keys allowed per validator is **1/3 of total external seats** \(network level\)

Note that validators sometimes choose to run duplicate instances \(2 instances, each running with same BLS key\) as a backup mechanism.

## Multi-BLS keys

Validators are not required to use the multiBLS feature in order to add multiple keys to their validator. Take a look at some possible scenarios in the illustration at the top. There are some differences to using multiBLS vs. single-key instance:

* Machine cost will be lower in a multiBLS instance \(compare 'validator 2' vs. 'validator 1'\)
* Single-key instances could run nodes for a validator in different shards, whereas a multiBLS instance requires all BLS keys to be in the same shard
* MultiBLS and single-key instance have different staking commands
* In order to make changes to the keys in a multiBLS instance, the node needs to be stopped and restarted; whereas a single-key instance can be directly added to a validator \(since the node is running on a different instance\)
* Too many bls keys signing using a single node creates a single point of failure \(validator’s risk\)

## 

### Shard Assignment

After a validator is elected, each of its elected BLS keys will be semi-randomly assigned to a shard in the network \(fully random shard assignment will come in the final phase of mainnet\). In the current stage of mainnet, the rule of assignment is simply based on the modulus of the BLS public key’s underlying bytes. For example, with 4 shards, a BLS public key like “xxxxxx8ad5” will be assigned to shard 1 because 5 % 4 = 1. Note that, for each of the elected BLS keys, the validator is obligated to spin up a validator node and validate blocks in the assigned shard.

