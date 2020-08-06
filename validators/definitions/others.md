# Slashing

{% embed url="https://www.youtube.com/watch?v=QvU67LFnb50&list=PLAzkb1vJXQOR3ZEl25MKiz5-CMw6xVkaW&index=6" %}

Slashing is an integral component of EPoS which serves as the deterring factor to prevent any non-conforming behaviors from validators such as double signing and being offline. 

If validators breach the protocol in the two ways:

1. Unavailability — a validator temporarily loses his slot if he misses more than 1/3 of the blocks in an epoch; this unresponsiveness is due to nodes being offline, largely not malicious behavior.
2. Double signing -- a validator loses at least 2% of the stake depending on how many slots are corrupted; this behavior is considered a malicious behavior.

A fraction of the staked tokens is slashed as penalties.Slashing penalties are imposed on both validators and delegators.

### **Uptime and Unavailability Penalty** <a id="e90a"></a>

The elected validators are obligated to validate blocks with their elected BLS keys. In every epoch, an elected validator should sign more than 2/3 of the signatures that its BLS keys are asked to sign.

The signing performance is represented by a percentage value called **uptime**. A validator’s uptime is the ratio of the number of signatures its elected BLS keys signed over the total number of signatures the keys should sign. For example, a validator has 2 elected BLS keys and each of the keys is presented 100 blocks to sign. In the final tally, the first key signed 70 blocks and the second key signed 80 blocks. Overall, the validator’s uptime is \(70+80\) / \(100\*2\) = 75%.

At the end of each epoch, the validators with uptime of no more than 2/3 \(66.66%\) will have their status set to “Inactive” and be ruled out from the new election. For these inactive validators, they are required to manually set their status to “Active” by sending an **EditValidator** transaction in order to participate in future elections. We encourage validators to be proactive in maintaining a high uptime to ensure they remain elected and earn the most block reward possible.

### Double Sign Slashing <a id="258b"></a>

If any BLS key\(s\) are detected signing conflicting blocks \(i.e. blocks with the same height and view ID but with different block hashes\), the validator will be slashed and forever banned from the network. When a validator is slashed, a certain percentage \(i.e. slashing rate\) of staked tokens from the validator and its delegators will be forfeited, of which half will be burnt and another half will be credited to the reporter of the double sign event.

The slashing rate is calculated by simply summing all the voting power of the double signing keys with a minimum of 2%. For example, if 3 BLS keys with voting power of 3%, 3% and 4% double signed at the same time, 10% of all staked tokens will be slashed on the validators who hold the 3 BLS keys.

