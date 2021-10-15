# Epoch Transition

In Harmony mainnet, there are 4 shards each producing new blocks separately and in parallel. The block heights between shards are not synchronized so you will see different shards have different block heights.

An epoch is a period of time when the beacon shard (i.e. shard 0, the coordinator for other shards) produces a fixed number of blocks. In Harmony mainnet, an epoch is **32768** blocks (\~18.2h with a 2s block time) in the beacon shard. Once an epoch is completed in the beacon shard, that change is also passed onto the other shards, thus all shards are synchronized by epoch.

At the end of each epoch, the committee election process will take place to elect the committees for the next epoch. The election process takes into account all the staking transactions confirmed before the election happens. The election result will take effect immediately, so we encourage all candidate validators to spin up their nodes even before the election happens.
