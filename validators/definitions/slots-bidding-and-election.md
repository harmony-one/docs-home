# Slots Bidding and Election

In Open Staking of mainnet, there will be 320 slots available for bidding. A slot represents membership in the network which gives the validator the right to use a specific BLS key to sign on blocks and the signature will be acknowledged by other validators.

After you create the validator record, the tokens you stake, along with any delegated tokens to your validator, will be automatically used to bid for the slots.

Each of the added BLS keys will create a unique bid for a slot in the network. The bid price equals the total stake on your validator divided by the total number of BLS keys attached to your validator.

Simply put, all tokens staked to the validator will be equally divided into each BLS key and each key bids separately. For example, a validator with a total stake of 300 ONE and 3 associated BLS keys will have 3 bids each with a bid price of 100 ONE.

The election for the slots works as follows.

1. Before the start of an epoch, all validator bids are ranked by bid price in descending order.
2. The highest 320 bids will be awarded the slots in the upcoming epoch.

The BLS key that successfully bids for a slot is deemed **elected**. Elected BLS keys will eventually form the committees of the shards. A validator in possession of at least one elected BLS key is also deemed **elected.**

![](../../.gitbook/assets/image%20%28120%29.png)

Above is a simple example of bidding and election process with 10 slots and 5 validators. 

