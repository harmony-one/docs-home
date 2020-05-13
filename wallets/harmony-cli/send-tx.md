# Sending transactions

Perhaps the most important feature of the `hmy` CLI is the ability to create and send signed transactions to the `Harmony` blockchain.

## Overview <a id="quick-version"></a>

### Sending a transaction <a id="sending-a-cross-shard-transaction-on-betanet"></a>

#### Using the Binary:

```bash
./hmy transfer --node="<endpoint-address>" \
 --from <ONE_address> --to <ONE_address> \
 --from-shard <shard> --to-shard <shard> \
 --amount <amount> --chain-id <chain-id> --passphrase
```

#### Using the Shell Script:

```bash
./hmy.sh -- transfer --node="<endpoint-address>" \
 --from <ONE_address> --to <ONE_address> \
 --from-shard <shard> --to-shard <shard> \
 --amount <amount> --chain-id <chain-id> --passphrase
```

#### Example:

```bash
./hmy --node="https://api.s0.t.hmny.io" \
 transfer --from one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw \
 --to one1q6gkzcap0uruuu8r6sldxuu47pd4ww9w9t7tg6 \    
 --from-shard 0 --to-shard 1 --amount 12.5 --chain-id mainnet --passphrase mypassword
```

### Checking the transaction hash <a id="checking-the-transaction-hash"></a>

Check for finality of the transaction by using the transaction hash like so:

#### Using the Binary:

```bash
./hmy blockchain transaction-receipt <transaction_id> --node="<endpoint-address>"
```

#### Using the Shell Script:

```bash
./hmy.sh -- blockchain transaction-receipt <transaction_id> --node="<endpoint-address>"
```

#### Example:

```bash
./hmy --node="https://api.s0.t.hmny.io" \
 blockchain transaction-receipt \
 0x599793f313ee17566f8d09728b9d043b8e26135ddce86beeee13f98767d452f7
```

## Detail <a id="tutorial"></a>

### ChainIDs <a id="chainids"></a>

Let's first check what chain-ids are available for us to use, we can do that easily with:

#### Using the Binary:

```bash
./hmy blockchain known-chains
```

#### Using the Shell Script:

```bash
./hmy.sh -- blockchain known-chains
```

#### Example:

```bash
./hmy blockchain known-chains

[
  "mainnet",
  "testnet",
  "devnet"
]
```

Notice that the output is pretty printed `JSON`, most outputs of `hmy` are `JSON` encoded and `hmy` defaults to showing it nicely indented. Sometimes though you might want to turn that off, you can do that for any command with the flag `--no-pretty`.

By default, `hmy` assumes the `testnet` chain-id; override that with the `--chain-id` flag

### Our first transaction <a id="our-first-transaction"></a>

We'll use the `transfer` subcommand of `hmy` to send a transaction.

```text
./hmy transfer
Error: required flag(s) "amount", "from", "from-shard", "to", "to-shard" not set
```

Notice that simply invoking the `transfer` subcommand gave us an error message about certain flags not being set. We'll need to provide legitimate values for these flags for our transaction to proceed successfully. Reading off the flags in the error message from left to right, the semantic meanings are as follows:

* `amount`: The quantity of Harmony One token to transfer from the senders to the receiver
* `from`: The sender's one address
* `from-shard`: Shard from which sender's balance will be drawn from
* `to`: Receiver's ONE address
* `to-shard`: Shard in which receiver will receive the amount sent by the sender
* `passphrase:` your wallet passphrase, which is prompted when you hit enter \(or you can use a txt file with password and add it: --passphrase file.txt\)

A sharded blockchain is a new kind of blockchain architecture where the network is partitioned into sub-networks called shards. Sharding is one of the distinguishing features of Harmony and it is key to solving the traditional scalability problems encountered in other blockchain protocols.

**Note:** The same ONE address will have a different balance in each shard. Currently Harmony mainnet has four shards while testnet has three shards. Sending a transaction from one shard to another is called a _"cross-shard transaction."_

Thus, a correct usage of `transfer` looks like:

#### Using the Binary:

```bash
./hmy transfer --node="<endpoint-address>" \
 --from <ONE_address> --to <ONE_address> \
 --from-shard <shard> --to-shard <shard> \
 --amount <amount> --chain-id <chain-id> --passphrase
```

#### Using the Shell Wrapper:

```bash
./hmy.sh -- transfer --node="<endpoint-address>" \
 --from <ONE_address> --to <ONE_address> \
 --from-shard <shard> --to-shard <shard> \
 --amount <amount> --chain-id <chain-id> --passphrase
```

#### Example:

```bash
./hmy transfer --node="https://api.s0.t.hmny.io" \
 --from one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw \
 --to one1q6gkzcap0uruuu8r6sldxuu47pd4ww9w9t7tg6 \
 --from-shard 0 --to-shard 1 --amount 10 --chain-id mainnet
{"transaction-receipt":"0x455f98a3aa11ef50ee5cc5ac8bbd79e04f2fe353180bb7e25fc6c921fc8fdc83"}
```

{% hint style="info" %}
`hmy` assumes that the private keys needed for signing the transaction on behalf of the sender \(`one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw` in this example\) exist in the local keystore or in the hardware wallet if the `--ledger` flag was used.
{% endhint %}

{% hint style="info" %}
The sender's account must have enough of a balance on the `from-shard` to send a transaction. In our example,`one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw` must have an amount balance of at least 10 in shard 0.
{% endhint %}

Try out your transaction with the flag `--dry-run`, this flag tells `hmy` to create, cryptographically sign the transaction but not actually send it off. Sender's balances are checked and the output is a JSON dump of the signed transaction.

Signing and sending a transaction is very quick, about 2 seconds maximum. The actual sending of the transaction is done via an `RPC` \(Remote Procedure Call\), you'll notice that we did not explicitly say where to send the transaction to. This is because the default destination of the `RPC` call goes to `http://localhost:9500`, the default `HTTP` `RPC` server running when you start a local harmony blockchain. For real world usage though, you'll want a different location. You can control that with the `--node` flag \(see the top of this page for an example\).

### Result of the transaction <a id="result-of-the-transaction"></a>

Once an `RPC` machine receives a transaction, it sends you back a transaction hash. This transaction hash is the key identifier used when querying the blockchain for transactions.

{% hint style="warning" %}
Simply having a transaction hash does NOT imply that the transaction was successfully accepted by the blockchain. A transaction is successfully accepted once it has been added to the blockchain. In the case of cross-shard transactions \(when the from-shard, to-shard values are different\), this means each shard has added the transaction to their blockchain.
{% endhint %}

We can pull down details of the finalized transaction with `./hmy blockchain transaction-receipt` as well:

#### Using the Binary:

```bash
./hmy blockchain transaction-receipt --node="<endpoint-address>" <transaction-hash>
```

#### Using the Shell Wrapper:

```bash
./hmy.sh -- blockchain transaction-receipt --node="<endpoint-address>" <transaction-hash>
```

#### Example:

```text
./hmy blockchain transaction-receipt \
    --node="https://api.s0.t.hmny.io" \
    0x25dd32397b5a69146b2dc3bbdc8ef8aae271e9b12a36c6dff1eb8995cac9dcba
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0x67eb5d671af76814d9ab326f9ec36c5b889b872e0c34e8cbe484aea20f0611ea",
    "blockNumber": "0x21017f",
    "contractAddress": null,
    "cumulativeGasUsed": "0x5208",
    "from": "one1sp4q22r7cc78742mzrufu6xwcekqxjgq78jk3m",
    "gasUsed": "0x5208",
    "logs": [],
    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "shardID": 0,
    "status": "0x1",
    "to": "one129r9pj3sk0re76f7zs3qz92rggmdgjhtwge62k",
    "transactionHash": "0x25dd32397b5a69146b2dc3bbdc8ef8aae271e9b12a36c6dff1eb8995cac9dcba",
    "transactionIndex": "0x0"
  }
}
```

{% hint style="info" %}
If the transaction has not finalized then the `"result"` key in the `JSON` output will have value of `null`.
{% endhint %}

{% hint style="warning" %}
You should set the value of `--node` to the same shard that sent the transaction, notice that the URL we used, `https://api.s0.t.hmny.io` contained `s0`, this means that this URL is targeting shard 0. For further information, see [Querying the Blockchain](querying-the-blockchain.md).
{% endhint %}

You can tell `hmy` to wait until transaction confirmation by providing a positive integer value to flag `--wait-for-confirm`. For example, `--wait-for-confirm=10` will try checking the receipt of the transaction for 10 seconds.

