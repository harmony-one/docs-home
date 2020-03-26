---
description: Here are the key definitions that validators and delegators should understand.
---

# Definitions

## **Multikey** 

A validator can take one or multiple validating slots in the network by putting stake into the slots and participating in the EPoS ranking.   


She can register with multiple bls keys by spinning up a node for each of the bls keys to sign blocks and earn reward. 

* Up to 1/3 of the total external slots available can be added to this validator. \(Total external slots available on mainnet is 320, so 106 keys you can add per validator\). 
* If you are running multiple slots, each slot has the same total stake \(your total stake / num of slots\).
* Each slot will rank in the EPoS individually, so there can be the case where some of the validator’s slots are selected in the committee while the rest are not.
* Each slot then earns its own rewards, which will get added to your validator account for you to collect.

She can also utilize a single node \(or a small set of nodes\) to sign for multiple bls keys. 

* One harmony binary \(or one machine\) can serve up to 4 slots. 
* Multiple bls keys on the same node must belong to the same shard. The node that is signing for multiple bls keys only runs a single consensus and maintains a single blockchain for the shard.
* Reduces the infrastructure cost for Harmony nodes \(~60%\). There is some non-trivial overhead on the single machine that is serving multiple slots but the cost of the second/ third/ fourth machine is saved. 
* Too many bls keys signing using a single node creates a single point of failure \(validator’s risk\).

## State Pruning

State pruning is a feature we implemented in harmony nodes to prune redundant state nodes from the state DB before it was written to the DB. State pruning will reduce the blockchain size from current 80+G \(as of Feb/25/2020\) to &lt;2G. Validators can reduce the disk size significantly to save the cloud cost. You can refer to ethereum’s [State Tree Pruning](https://blog.ethereum.org/2015/06/26/state-tree-pruning/).  


## Slashing

Slashing is an integral component of EPoS which serves as the deterring factor to prevent any non-conforming behaviors from validators such as double signing and being offline. 

If validators breach the protocol in the two ways:

1. Unavailability — a validator temporarily loses his slot if he misses more than 66% of the blocks in an epoch; this unresponsiveness is due to nodes being offline, largely not malicious behavior.
2. Double signing -- a validator loses at least 2% of the stake depending on how many slots are corrupted; this behavior is considered a malicious behavior.

A fraction of the staked tokens is slashed as penalties.Slashing penalties are imposed on both validators and delegators.

## Availability / Unavailability \(Down Time\)

If a validator signed less than 66% of the total number of blocks \(from all the slots of this validator\) he should’ve signed in one epoch, the validator will be put into inactive mode. Inactive validators will not be included in the next epoch shard assignment.

An inactive validator will be eligible to be elected again after it is edited as “active”.

There will be no slashing on stake for unavailability as they are already punished by missing out the block rewards.

## Double Signing

Double signing is a bad situation when a validator node signs an alternative vote to the canonical one\(conflicting blocks are detected\). This is considered a purposefully malicious attack thus the offender must be penalized in such a scenario.

If conflicting blocks are detected, anyone seeing such block can send a Slash message to prove the misbehavior:

The double signer\(s\) proved to be guilty will have their stake slashed and forever banned from the network since the next epoch. If further double signing happens before that\(in the current epoch\), slashing will trigger again on the validator with the same slashing rule.

The slashing rate is determined by the percentage of double signers among all the signers on the same block with a minimum slashing rate of 2%. For example, if there is only one double signer, the slashing rate will be 2%. If there are 5 double signers among a committee of 100 signers, the slashing rate will be 5%.

In the case of a validator having multiple BLS keys, each key is treated as a signer and if any key double signs, the validator will be slashed as a whole.

The slashed token will be half burned and half credited to the reporter’s balance.





