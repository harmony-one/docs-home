# Adding Harmony

### Adding Harmony to Rabby Wallet

Note: Harmony is installed on Rabby Wallet by default. The application automatically switches networks once you connect it to a Harmony dApp. However, older versions may not have Harmony added yet. Please follow the steps below to manually add the network.

Open Rabby Wallet and click the list of networks at the top, then select "More".

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-11-27 at 13.57.49.png" alt="" width="375"><figcaption><p>Select "More"</p></figcaption></figure>

Then select "Add Custom Network"

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-11-27 at 14.03.11.png" alt="" width="375"><figcaption><p>Select "Add Custom Network"</p></figcaption></figure>

### Fill the Endpoint Information

You will be prompted for additional information. Use the table below to complete the step. Below you will see multiple options for RPC URL and Chain ID corresponding to mainnet vs testnet, and the various shards within each.



Alternatively, use the "Quick Add" option via Chainlist and search for "Harmony"

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-11-27 at 14.07.04.png" alt="" width="365"><figcaption><p>Quick Add from Chainlist</p></figcaption></figure>

{% hint style="info" %}
**Use the RPC URL and Chain ID of Shard 0 if you want to send/receive transactions from exchanges or do any staking transaction type.**
{% endhint %}

| Field                                                    | Mainnet                                                                        | Testnet                                                                       | Devnet                                                        |
| -------------------------------------------------------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- | ------------------------------------------------------------- |
| **Network Name**                                         | Harmony Mainnet                                                                | Harmony Testnet                                                               | Harmony Devnet                                                |
| **New RPC URL**                                          | <p>https://api.harmony.one</p><p>https://s1.api.harmony.one</p><p></p>         | <p>https://api.s0.b.hmny.io</p><p>https://api.s1.b.hmny.io</p>                | <p>https://api.s0.ps.hmny.io<br>https://api.s1.ps.hmny.io</p> |
| <p><strong>Chain ID</strong></p><p>(use number only)</p> | <p>Shard 0: <code>1666600000</code></p><p>Shard 1: <code>1666600001</code></p> | <p>Shard 0: <code>1666700000</code><br>Shard 1: <code>1666700001</code></p>   | <p>Shard 0: 1666900000<br>Shard 1: 1666900001</p>             |
|                                                          |                                                                                |                                                                               |                                                               |
| **Currency symbol (optional)**                           | ONE                                                                            | ONE                                                                           | ONE                                                           |
| **Block Explorer URL (optional)**                        | [https://explorer.harmony.one/](https://explorer.harmony.one/)                 | [https://explorer.testnet.harmony.one/](https://explorer.testnet.harmony.one) | [https://explorer.ps.hmny.io](https://explorer.ps.hmny.io)    |

The example below shows the configuration that needs to be done to connect to Harmony Mainnet on Shard 0:

![](<../../../../../.gitbook/assets/image (294) (1) (2) (2) (1) (2) (2) (2) (2) (2) (2) (2) (2) (3) (3) (3) (1) (1) (1) (2) (1) (1) (3).png>)

Click the Save button and your configuration should be done!

{% hint style="success" %}
if you have any issue fetching data like chain-id, try to type the `new RPC URL` instead copy pasting it.
{% endhint %}
