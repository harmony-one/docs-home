# Validator, keys and bids

#### Validator

A validator technically represents a single one1.. account \(address\) that was entered into a successful create-validator transaction. Once a one1.. address is registered as a validator, the earnings of validator goes to this one1.. account.

#### BLS key\(s\)

A BLS key represents what the validator signs the blocks with, and is the way of authenticating the validator. A validator can have multiple keys to sign with, it means that this validator is signing blocks in parallel.

BLS keys are attached to validator via:

* Creating a new validator \(put commas between BLS keys\)
* Adding new keys to an existing validator

#### Instance\(s\)

An instance is a virtual machine session with a unique IP address. Within each instance, there could be up to 4 BLS keys signing transactions. If you have more than a single BLS key in your instance, it means that you're using the **multiBLS feature**. If you have a single BLS key in the instance, we will call that single-key instance.

Here are **some rules to follow:**

* In order to use multiBLS feature \(multiple BLS keys in same instance\), all keys are required to be on the **same shard**
* Total number of BLS keys allowed per validator is **1/3 of total external seats** \(network level\)

Note that validators sometimes choose to run duplicate instances \(2 instances, each running with same BLS key\) as a backup mechanism.

#### Important message

Validators are not required to use the multiBLS feature in order to add multiple keys to their validator. Take a look at some possible scenarios in the illustration below. There are some differences to using multiBLS vs. single-key instance:

* Machine cost will be lower in a multiBLS instance \(compare 'validator 2' vs. 'validator 1'\)
* Single-key instances could run nodes for a validator in different shards, whereas a multiBLS instance requires all BLS keys to be in the same shard
* MultiBLS and single-key instance have different staking commands
* In order to make changes to the keys in a multiBLS instance, the node needs to be stopped and restarted; whereas a single-key instance can be directly added to a validator \(since the node is running on a different instance\)

![](../../.gitbook/assets/image%20%2838%29.png)

![](../../.gitbook/assets/image%20%2828%29.png)

