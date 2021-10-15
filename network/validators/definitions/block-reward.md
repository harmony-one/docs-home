# Block Reward

For each of the blocks produced and confirmed within a shard, it should contain signatures from the keys with more than 2/3 of the total voting power of the shard committee. Each confirmed block will produce 28 ONE as block reward for the validators behind the committee. The 28 ONE is initially allocated to all the validators whose BLS key(s) signed on the block, proportionally to the voting power of the key(s) that signed.

The allocated block reward for a validator will be further distributed to delegators proportionally to their stake after the commission fee is charged. For example, a validator with a commission rate of 25% got allocated 4 ONE for a block it signed. The validator staked 1000 ONE itself and it has 2 delegations each with 1000 ONE. The block reward distribution for this validator works as follows:

1. The commission fee of 1 ONE (4 ONE \* 25%) is cut from the original reward and credited to the validator.
2. The rest of the reward of 3 ONE is then distributed to all the stakers (including both the validator and its delegators) proportionally based on their stake. Since the stakers (the validator and the two delegators) each staked/delegated 1000 ONE, they each receive 1 ONE in the reward distribution.

For more information about block reward, please read our [token economics model](https://medium.com/harmony-one/harmonys-new-tokenomics-bcdac0db60d7).
