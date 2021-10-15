# Sharding

Harmony blockchain is sharded in three dimensions: state, network and transaction. 

**State Sharding**

In Harmony, each shard maintains it's own chain of blocks and state database. Therefore, the validators of each shard only need to store 1/N of the global state, where N is the number of shards. The consistency between states from different shards are guaranteed by the property of eventual atomicity of cross-shard transactions, which guarantees that double spending between shards can not happen.

**Network Sharding**

Harmony's validator network is also divided into shards where each shard involves a separate set of validators connected closely with each other and running consensus between themselves. Most of the time, validators communicate with other validators within the same shard to reach consensus or synchronize blocks. In cases of cross-shard transactions and beacon chain synchronization, validators from different shards send messages across shards through the globally connected network.

**Transaction Sharding**

Transactions in Harmony blockchain are sent to and processed by a specific shard instead of all shards. This way, shards can process transactions in parallel which greatly improves the overall transaction processing capacity of the blockchain. Users need to specify a field named `shard_id` in the signed transaction which indicates which shard this transaction belongs to. For cross-shard transactions, another field named `to_shard_id`is needed to indicate the destination shard while the `shard_id` field indicates the source shard. 

## Epochs

An epoch in Harmony blockchain is a pre-determined period of time when the validator committees of  shards stay unchanged. **In Harmony mainnet, one epoch is 32768 blocks which translates to around 18.2 hours. **In Harmony testnet, one epoch is 8192 blocks which is around 4.6 hours.

When one epoch ends, the election for the new validator committees will be conducted in beacon chain and the result (i.e. shard state) will be written in the last block of the epoch in the beacon chain. After that, beacon chain enters the new epoch with the new validator committee producing blocks. Once beacon chain enters new epoch, all the other shards will follow and also enters the new epoch. The new shard state from the beacon chain will be written in the new block of the shards which also marks the last block of the epoch for that shard.

## **Crosslinks**

Crosslink is an important piece of data which is sent from shard chains and stored in beacon chain. A crosslink contains data for block signatures and the block identifier data such as block hash, block number, view id and epoch etc. When a new block is confirmed in a shard chain, the corresponding crosslink will be created and sent to the beacon chain. Upon the receipt of the crosslink, the beacon chain verifies its signature and checks that it’s from the canonical chain of the shard. Successfully verified crosslinks will be added in the new block of the beacon chain to permanently endorse the block of the shard chain as canonical. Shard chain blocks without corresponding crosslinks endorsed in the beacon chain won’t be recognized by the network and will be deemed as invalid blocks.

![](<../../.gitbook/assets/image (230).png>)

Besides serving the purpose of marking canonical blocks of the shard chains, crosslinks are also used to record and tally the signing activity of the shard chain validators. Since epoch transition and EPoS election happens only on beacon chain, the validator signing activity from shard chains are sent to the beacon chain via the crosslink so it can be used for block reward calculation and uptime calculation which affect the validator’s election status.\
