# List of Transaction Error Messages

Here is the list of failed transaction messages which can be checked by querying your transaction hash, checking the transaction hash on explorer or checking the blockchain pool transactions.

Here is how with the hmy cli :

{% tabs %}
{% tab title="Linux" %}
```bash
./hmy failures plain --node="https://api.s0.t.hmny.io"
```
{% endtab %}

{% tab title="MacOS" %}
```bash
./hmy.sh -- failures plain --node="https://api.s0.t.hmny.io"
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
failed messages are network and shard specifics, please use the shard you were sending the transaction from and change the --node value accordingly.\
Mainnet example on shard 1 would be : https://api.s1.t.hmny.io
{% endhint %}

| **Message**                                                                                          | **Notes**                                                                                               |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| transaction size is \<tx size in Bytes>: oversized data                                              | A transaction cannot be more than 32KB to prevent DDOS attacks                                          |
| transaction value is \<tx value>: negative value                                                     | Transaction value is negative                                                                           |
| transaction gas is \<tx gas-limit>: exceeds block gas limit                                          | Assumed to be hardcoded / config                                                                        |
| transaction sender is \<tx from addr>: invalid sender                                                | Transaction sent from an invalid account                                                                |
| transaction gas-price is \<tx gas-price> ONE: transaction underpriced                                | Too low transaction fee                                                                                 |
| transaction nonce is \<tx nonce>: nonce too low                                                      | Occurs when the nonce associated with that transaction is too lower than the actual nonce               |
| insufficient funds for gas \* price + value                                                          | Usually when not enough holdings to pay for gas                                                         |
| transaction gas is \<tx gas-limit>: intrinsic gas too low                                            | Intrinsic gas is based on the size of the transaction including data                                    |
| transaction gas-price is \<tx gas-price> ONE in full transaction pool: transaction underpriced       | Transactions can get dropped if tx pool is full and tx has lowest gas                                   |
| existing transaction price was not bumped enough: replacement transaction underpriced                | If a transaction attempts to replace another with less gas than the original, it will get dropped       |
| old transaction, nonce \<tx nonce> is too low                                                        | During promotion (from 'future' txs to pending txs in pool) the nonce is checked again                  |
| unpayable transaction, out of gas or balance of \<acc bal in ONE >cannot pay cost of \<cost on ONE>  | During promotion (from 'future' txs to pending txs in pool) balance is checked again                    |
| exceeds cap for queued transactions for account \<one1... address>                                   | Each account has a limit in the number of txs it can put into the tx pool                               |
| fairness-exceeding pending transaction                                                               | If tx pool is full, txs from accounts with highest number of total transactions in pool will be dropped |
| exceeds global cap for queued transactions                                                           | Occurs when the tx can´t be queued because global cap for queued tx pool exceeds the max                |
| old transaction, nonce \<tx nonce> is too low                                                        | During demote (from pending txs in pool to 'future' txs) the nonce is checked again                     |
| unpayable transaction, out of gas or balance of \<acc bal in ONE > cannot pay cost of \<cost in ONE> | During demote (from pending txs in pool to 'future' txs) balance is checked again                       |
| demoting pending transaction                                                                         | Tx was not added to the pool and move to queue of 'future' txs                                          |
