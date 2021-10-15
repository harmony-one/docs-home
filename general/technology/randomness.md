# Randomness

Harmony’s sharding approach depends on a secure randomness source so the validators can be assigned to shards in a truly random manner to avoid single-shard attacks. Harmony designed a distributed randomness generation (DRG) protocol which involves both VRF (Verifiable Random Function) and VDF (Verifiable Delay Function) to achieve the follows key properties:  

1. Unpredictable: No one should be able to predict the random number before it is generated.
2. Un-biased: The process of generating the random number should not be biasable by any participant.
3. Verifiable: The validity of the generated random number should be verifiable by any observer.
4. Scalable: The algorithm of randomness generation should scale to a large number of participants.

Since the random assignment (resharding) of validators only happens every epoch, Harmony’s DRG protocol only needs to execute once per epoch. It works as follows:

1. During the epoch, each validator takes turns to become the FBFT leader and at the end of the epoch, all validators should have become leader for at least once. Each new leader runs VRF to create a random number R and a proof P using its BLS key. The random number and the proof will be attached to the first proposed block by the leader, which will be verified by the validators and committed to the blockchain.
2. As soon as more than 2/3 of the validators have done the VRF submission, the immediate next leader will combine all the submitted random numbers with an XOR operation to get the preimage pRnd of the final randomness.
3. The leader runs FBFT among all the validators to reach consensus on the pRnd and commit it in block.
4. After pRnd is committed, the leader starts computing the actual randomness Rnd=VDF(pRnd, T), where T is the VDF difficulty and is set algorithmically such that the randomness can only be computed after k blocks.
5. Once Rnd is computed, the leader initiates a FBFT among all validators to agree on the validity of Rnd and finally commit the randomness into the blockchain.

![The VDF (Verifiable Delay Function) delays the revelation of the final randomness.](https://lh3.googleusercontent.com/nO_rCzf7LjFBS9ZyhC_RHKX5OSRH0jj5vMusM9dluDumYZSLkGtUBpDpiQ7xsnV79mKYuTCjMXE_aL9Da3IvUir02m0zxYvgxvYcSqxD1ADEOD-WzWkNrJyWq1JQFqQZvxyvr6rP)

The VDF (Verifiable Delay Function) is used to delay the revelation of the final randomness in order to be secure against last-revealer-attack.The VDF is used to provably delay the revelation of Rnd and prevent the last leader from biasing the randomness by choosing to submit or not the last random number. Because of the VDF, the last leader won’t be able to know the actual final randomness before pRnd is committed to the blockchain. By the time Rnd is computed with the VDF, pRnd is already committed in a previous block so the leader cannot manipulate it anymore. Therefore, the most a malicious leader can do is to either blindly commit the randomness pRnd, or stall the protocol by not committing pRnd. The former is the same as the honest behavior. The latter won’t cause much damage as the timeout mechanism in FBFT will be triggered to switch the leader.

