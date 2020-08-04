# Validators

Harmony is one of the first production mainnets to feature a fully sharded PoS architecture. Across the 4 shards in Harmony mainnet, blocks are produced every 8 seconds and cross-shard transactions are finalized in 2 block times.

Currently there are 320 open validator slots, 80 on each shard, to validate new blocks and vote to reach consensus using our FBFT algorithm where a 2/3 quorum of votes is needed for consensus.To be able to vote, validators need to have voting shares bonded to them. One bonded voting share grants one vote for a validator to cast in the FBFT consensus. As detailed in our [whitepaper](https://harmony.one/whitepaper), Harmony blockchain runs in epochs and one epoch lasts for every 16,384 blocks, which is roughly 1.5 days in current block time. Within an epoch, the validators in each shard stay the same and run consensus repeatedly.

Harmony’s Effective Proof-of-Stake \(EPoS\) is the first staking mechanism in a sharded blockchain that achieves both security and decentralization. EPoS allows staking from hundreds of validators and the unique **effective stake** mechanism reduces the tendency of stake centralization. Meanwhile, stake delegation, reward compounding, double-sign slashing, and unavailability checking are also supported.

 

{% page-ref page="definitions/" %}

{% page-ref page="cloud-setup/" %}

{% page-ref page="autonode/" %}

{% page-ref page="first-time-setup/" %}

{% page-ref page="managing-your-validator/" %}

{% page-ref page="staking-dashboard.md" %}

{% page-ref page="first-time-setup/validator-cheat-sheet.md" %}

{% page-ref page="validator-troubleshooting/" %}

