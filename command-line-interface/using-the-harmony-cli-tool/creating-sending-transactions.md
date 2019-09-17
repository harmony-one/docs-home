---
description: Transactions on Harmony
---

# Creating, sending transactions

Perhaps the most important feature of the `hmy` CLI is the ability to create and send signed transactions to the `Harmony` blockchain.

## Quick version

### Sending a cross-shard transaction on betanet:

```text
$ hmy --node="https://api.s0.b.hmny.io/" \
    transfer --from one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw \
    --to one1q6gkzcap0uruuu8r6sldxuu47pd4ww9w9t7tg6 \
    --from-shard 0 --to-shard 1 --amount 12.5
```

{% hint style="info" %}
Same shard transactions require the same shard value used in the `--from-shard` and `--to-shard` flags.
{% endhint %}

### Checking the transaction hash

Check for finality of the transaction by using the transaction hash like so

```text
$ hmy --node="https://api.s0.b.hmny.io" \
    blockchain transaction-receipt \
    0x599793f313ee17566f8d09728b9d043b8e26135ddce86beeee13f98767d452f7
```

## Tutorial

### ChainIDs

Let's first check what chain-ids are available for us to use, we can do that easily with:

```text
$ hmy blockchain known-chains
[
  "mainnet",
  "testnet"
]
```

{% hint style="info" %}
Notice that the output is pretty printed `JSON`, most outputs of `hmy` are `JSON` encoded and `hmy` defaults to showing it nicely indented. Sometimes thought you might want to turn that off, you can do that for any command with the flag `--no-pretty`.
{% endhint %}

{% hint style="info" %}
By default, `hmy` assumes the `testnet` chain-id; override that with the `--chain-id` flag
{% endhint %}

### Our first transaction

We'll use the `transfer` subcommand of `hmy` to send a transaction.

```text
$ hmy transfer
Error: required flag(s) "amount", "from", "from-shard", "to", "to-shard" not set
```

Notice that simply invoking the `transfer` subcommand gave us an error message about certain flags not being set. We'll need to provide legitimate values for these flags for our transaction to proceed successfully. Reading off the flags in the error message from left to right, the semantic meanings are as follows:

* `amount`: The quantity of Harmony One token to transfer from the senders to the receiver
* `from`: The sender's one address
* `from-shard`: Shard from which sender's balance will be drawn from
* `to`: Receivers one address
* `to-shard`: Shard in which receiver will receive the amount sent by the sender

{% hint style="info" %}
A sharded blockchain is new, special kind of blockchain where the whole network is partitioned between mutally exclusive shards. Sharding is one of the distinguishing features of Harmony and it is key to solving the tranditional scalability problems found in other blockchain protocols. Note that **a one address may and often does have a different balance in each shard**, currently mainnet has four shards while testnet assumes two shards; sending a transaction from one shard to another is called a ****_"cross-shard" transaction._
{% endhint %}

Thus, a correct usage of `transfer` looks like:

```text
$ hmy transfer --from one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw \
      --to one1q6gkzcap0uruuu8r6sldxuu47pd4ww9w9t7tg6 \
      --from-shard 0 --to-shard 1 --amount 10
```

The `\` is just a way to break lines in the shell, used in this example to make it easier to see. Some key points to note in this example:

1. `hmy` assumes that the private keys needed for signing the transaction on behalf

   of the sender \(`one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw` in this example\) exist

   in the local keystore or in the hardware wallet if the `--ledger` flag was used.

2. Although the sender's account may have enough of a balance across all shards, the relevant balance is the balance amount of the sender's account in the _from-shard_. In our example,`one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw` must have an amount balance of at least 10 in shard 0.

{% hint style="success" %}
Try out your transaction with the flag `--dry-run`, this flag tells `hmy` to create, cryptographically sign the transaction but not actually send it off. Sender's balances are checked and the output is a JSON dump of the ready to have been sent signed transaction.
{% endhint %}

Signing and sending the transaction is very quick, about two seconds maximum. The actual sending of the transaction is done via an `RPC` call, you'll notice that we did not explicitly say where to send the transaction to. This is because the default destination of the `RPC` call goes to `http://localhost:9500`, the default `HTTP` `RPC` server running when you start a local harmony blockchain. For real world usages though, you'll want a different location. You can control that with the `--node`, see the top of this page for an example.

### Result of the transaction

Once a `RPC` machine receives a transaction, it sends us back a transaction hash. This transaction hash is the key identifier we use when querying the blockchain about transactions.

{% hint style="info" %}
PROTIP: Simply having a transaction hash does NOT imply that the transaction was successfully accepted by the blockchain. A transaction is successfully accepted once it has been added to the blockchain, in the case of cross-shard transactions \(when the from-shard, to-shard values are different\), this means each shard has added the transaction to their blockchain.
{% endhint %}

We can pull down details of the finalized transaction with `hmy` as well, an example:

```text
$ hmy --node="https://api.s0.b.hmny.io" \
    blockchain transaction-receipt \
    0x599793f313ee17566f8d09728b9d043b8e26135ddce86beeee13f98767d452f7
```

Keep in mind two key points:

1. If the transaction has not finalized then the `"result"` key in the `JSON` output will have

   value of `null`.

2. You should set the value of `--node` to the same shard that sent the transaction, notice that the

   URL we used, `https://api.s0.b.hmny.io` contained `s0`, this means that this URL is targeting

   shard 0.

You can tell `hmy` to wait until transaction confirmation by providing a positve integer value to flag `--wait-for-confirm`. As an example, `--wait-for-confirm=10` will try checking the receipt of the transaction for 10 seconds.

