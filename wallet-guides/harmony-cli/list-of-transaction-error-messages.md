# List of transaction error messages

Here is the list of failed transaction messages which can be checked by querying your transaction hash, checking the transaction hash on explorer or checking the blockchain pool transactions.

Here is how with the hmy cli :

```bash
./hmy failures plain --node="https://api.s1.t.hmny.io"
```

{% hint style="info" %}
failed messages are network and shard specifics, please use the shard you were sending the transaction from and change the --node value accordingly

Example above is for shard 1 in the test network.   
Mainnet example on shard 0 would be : https://api.s0.t.hmny.io
{% endhint %}

| **Message** | **Notes** |
| :--- | :--- |
| transaction size is &lt;tx size in Bytes&gt;: oversized data | A transaction cannot be more than 32KB to prevent DDOS attacks |
| transaction value is &lt;tx value&gt;: negative value | Transaction value is negative  |
| transaction gas is &lt;tx gas-limit&gt;: exceeds block gas limit | Assumed to be hardcoded / config |
| transaction sender is &lt;tx from addr&gt;: invalid sender | Transaction sent from an invalid account |
| transaction gas-price is &lt;tx gas-price&gt; ONE: transaction underpriced | Too low transaction fee |
| transaction nonce is &lt;tx nonce&gt;: nonce too low | Occurs when the nonce associated with that transaction is too lower than the actual nonce   |
| insufficient funds for gas \* price + value | Usually when not enough holdings to pay for gas |
| transaction gas is &lt;tx gas-limit&gt;: intrinsic gas too low | Intrinsic gas is based on the size of the transaction including data |
| transaction gas-price is &lt;tx gas-price&gt; ONE in full transaction pool: transaction underpriced | Transactions can get dropped if tx pool is full and tx has lowest gas |
| existing transaction price was not bumped enough: replacement transaction underpriced | If a transaction attempts to replace another with less gas than the original, it will get dropped |
| old transaction, nonce &lt;tx nonce&gt; is too low | During promotion \(from 'future' txs to pending txs in pool\) the nonce is checked again |
| unpayable transaction, out of gas or balance of &lt;acc bal in ONE &gt;cannot pay cost of &lt;cost on ONE&gt; | During promotion \(from 'future' txs to pending txs in pool\) balance is checked again |
| exceeds cap for queued transactions for account &lt;one1... address&gt; | Each account has a limit in the number of txs it can put into the tx pool |
| fairness-exceeding pending transaction | If tx pool is full, txs from accounts with highest number of total transactions in pool will be dropped |
| exceeds global cap for queued transactions | Occurs when the tx can´t be queued because global cap for queued tx pool exceeds the max  |
| old transaction, nonce &lt;tx nonce&gt; is too low | During demote \(from pending txs in pool to 'future' txs\) the nonce is checked again |
| unpayable transaction, out of gas or balance of &lt;acc bal in ONE &gt; cannot pay cost of &lt;cost in ONE&gt; | During demote \(from pending txs in pool to 'future' txs\) balance is checked again |
| demoting pending transaction | Tx was not added to the pool and move to queue of 'future' txs |

