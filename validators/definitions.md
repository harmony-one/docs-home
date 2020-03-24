---
description: Here are the key definitions that validators and delegators should understand.
---

# Definitions

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





