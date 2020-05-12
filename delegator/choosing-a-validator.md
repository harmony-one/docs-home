# Choosing a Validator

In order to choose their validators, delegators have access to a range of information directly in [Lunie](https://lunie.io/) or other Cosmos block explorers.

* **Validator's moniker**: Name of the validator candidate.
* **Validator's description**: Description provided by the validator operator.
* **Validator's website**: Link to the validator's website.
* **Initial commission rate**: The commission rate on revenue charged to any delegator by the validator \(see below for more detail\).
* **Commission max change rate:** The maximum daily increase of the validator's commission. This parameter cannot be changed by the validator operator.
* **Maximum commission:** The maximum commission rate this validator candidate can charge. This parameter cannot be changed by the validator operator.
* **Minimum self-bond amount**: Minimum amount of Atoms the validator candidate need to have bonded at all time. If the validator's self-bonded stake falls below this limit, their entire staking pool \(i.e. all its delegators\) will unbond. This parameter exists as a safeguard for delegators. Indeed, when a validator misbehaves, part of their total stake gets slashed. This included the validator's self-delegateds stake as well as their delegators' stake. Thus, a validator with a high amount of self-delegated Atoms has more skin-in-the-game than a validator with a low amount. The minimum self-bond amount parameter guarantees to delegators that a validator will never fall below a certain amount of self-bonded stake, thereby ensuring a minimum level of skin-in-the-game. This parameter can only be increased by the validator operator.

