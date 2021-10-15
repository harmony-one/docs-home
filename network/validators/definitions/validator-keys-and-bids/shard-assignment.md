# Shard Assignment

After a validator is elected, each of its elected BLS keys will be semi-randomly assigned to a shard in the network (fully random shard assignment will come in the final phase of mainnet). In the current stage of mainnet, the rule of assignment is simply based on the modulus of the BLS public key’s underlying bytes. For example, with 4 shards, a BLS public key like “xxxxxx8ad5” will be assigned to shard 1 because 5 % 4 = 1. Note that, for each of the elected BLS keys, the validator is obligated to spin up a validator node and validate blocks in the assigned shard.
