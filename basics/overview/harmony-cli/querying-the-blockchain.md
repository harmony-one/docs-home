# Querying the blockchain

`hmy` provides several subcommands under the `blockchain` subcommand which let you query the blockchain.

{% hint style="info" %}
The Harmony blockchain is a _sharded_ blockchain, therefore some commands depend on which _shard_ you target. The shard you target when querying is controlled by the `--node` flag. For example, if a transaction is made between shard 0 and shard 1, the transaction receipt must be queried from whichever shard sent the funds - in this case shard 0, so the --node flag would look like this:

```text
--node="https://api.s0.t.hmny.io"
```

For other shards, please replace the **s0** with the appropriate shard number - eg. **s1** for shard 1, **s2** for shard 2 etc.
{% endhint %}

## List of available commands

By using `./hmy blockchain help` command we can see that the following options are available:

{% hint style="info" %}
* **block-by-number** - get a harmony blockchain block by block number
* **current-nonce** - current nonce of an account delegation information about delegations
* **known-chains** - print out the known chain-ids 
* **latest-header** - get the latest header
* **median-stake** - median stake of top 320 validators with delegations applied stake \(pre-epos processing\)
* **protocol-version** - the version of the Harmony Protocol
* **transaction-by-hash** - get transaction by hash
* **transaction-receipt**  - get information about a finalized transaction validator information about validators
* **pool** - get transaction pool information
{% endhint %}

Here are some examples of the above commands that you will use frequently:

### **transaction-by-hash**

Checking the hash of your transaction to see the transaction data and if the transaction has been completed

#### Using the Binary:

```text
./hmy blockchain transaction-by-hash <transaction-hash> --node="<endpoint-address>"
```

#### Using the Shell Wrapper:

```text
./hmy.sh -- blockchain transaction-by-hash <transaction-hash> --node="<endpoint-address>"
```

#### Example:

```text
./hmy blockchain transaction-by-hash 0x75d91100734edcd1497200cb438f0864d2ed4a44a88bf8c87855cb2b3cc54001 --node="https://api.s0.t.hmny.io"

{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0xf9c7e165d5636c7dd8a06bf2c53c364d7597028d7e10a3c5256462adf97b1f73",
    "blockNumber": "0xa35",
    "from": "one1mrrq665uarrmfur6hptevx9furph4293a37zme",
    "gas": "0x5208",
    "gasPrice": "0x3b9aca00",
    "hash": "0x75d91100734edcd1497200cb438f0864d2ed4a44a88bf8c87855cb2b3cc54001",
    "input": "0x",
    "nonce": "0xe",
    "r": "0x4a17d89f7b1818fe72d480a64fecfede1d73bd7242fcaabf907204a7022be806",
    "s": "0x557be1b9c378ecbae972e71ec6fc5d484abfe8cb7961ccd87724865c3a7020bc",
    "shardID": 0,
    "timestamp": "0x5e1cfcc1",
    "to": "one1mrrq665uarrmfur6hptevx9furph4293a37zme",
    "toShardID": 1,
    "transactionIndex": "0x0",
    "v": "0x2a",
    "value": "0xde0b6b3a7640000"
  }
}
```

### **transaction-receipt**

Get information about a finalized transaction:

#### Using the Binary:

```text
./hmy blockchain transaction-receipt <transaction-hash> --node="<endpoint-address>"
```

#### Using the Shell Wrapper:

```text
./hmy.sh -- blockchain transaction-receipt <transaction-hash> --node="<endpoint-address>"
```

#### Example:

```text
./hmy --node="https://api.s0.t.hmny.io" blockchain transaction-receipt 0x599793f313ee17566f8d09728b9d043b8e26135ddce86beeee13f98767d452f7

{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0x52171a8f3af94f639f1e6044679c4189c3cd088ffe7f1c216ce3089212373af9",
    "blockNumber": "0x6177",
    "contractAddress": null,
    "cumulativeGasUsed": "0x5208",
    "from": "0x261fa45c6a09cd3faa277d829e91d9473973357c",
    "gasUsed": "0x5208",
    "logs": [],
    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "shardID": 0,
    "status": "0x1",
    "to": "0x06916163a17f07ce70e3d43ed37395f05b5738ae",
    "transactionHash": "0x599793f313ee17566f8d09728b9d043b8e26135ddce86beeee13f98767d452f7",
    "transactionIndex": "0x0"
  }
}
```

### **latest-header command**

Checking the network status, last block, epoch, leaders, based on the shard number:

#### Using the Binary:

```text
./hmy blockchain latest-header --node="<endpoint-address>"
```

#### Using the Shell Wrapper:

```text
./hmy.sh -- blockchain latest-header --node="<endpoint-address>"
```

#### Example:

{% tabs %}
{% tab title="Shard 0" %}
```text
./hmy blockchain latest-header --node=https://api.s0.t.hmny.io

{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0xae23db112d22062be6a0f065ecc3989d4e9559ad6a1f34fe4344d021907e8c2e",
    "blockNumber": 415749,
    "epoch": 5543,
    "lastCommitBitmap": "fffffffffffffffb0f00",
    "lastCommitSig": "06efa677bdd327d3d9602fd246c214edb35e447692dccc2219ef08ce2fa026b96f3826fcb5a2a3f724222ecef4af66029f3b5d677e54534519ad2a405ad3b336dd5145dcc083fc2330b9d0bb398affd1745cab274b5019f32cba0287bd5e5a17",
    "leader": "one18ahxsrk9g4h4gz5r8ema7nyw6g9zpun5hhp54d",
    "shardID": 0,
    "timestamp": "2019-12-11 12:18:21 +0000 UTC",
    "unixtime": 1576066701,
    "viewID": 415745
  }
}
```
{% endtab %}

{% tab title="Shard 1" %}
```text
./hmy blockchain latest-header --node=https://api.s1.t.hmny.io

{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0x65d528672301b1c086b4f2db89ce20f6977f7aeaa494073352e211ac29f55179",
    "blockNumber": 456065,
    "epoch": 5543,
    "lastCommitBitmap": "ffffffffffffffff0f00",
    "lastCommitSig": "c8e049810c1f649625259f684e99f4a9cfc51cf01b2dd032f884136c9922ebb8fe0929e366bbf8122e430402d04d4804362013302994d4924c2990bdffeacb4b79e075c1897947a7ec5be44eef6f1bd1e013b80008f28085c15e17aa49629a09",
    "leader": "one1vaqzxt50ltk9hq4d44lgxmj4pj2x533fsp2acx",
    "shardID": 1,
    "timestamp": "2019-12-11 12:21:52 +0000 UTC",
    "unixtime": 1576066912,
    "viewID": 456065
  }
}
```
{% endtab %}

{% tab title="Shard 2" %}
```text
./hmy blockchain latest-header --node=https://api.s2.t.hmny.io

{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0xd5775e720a9bcc5a88fd13aac27d72365f4724d6a513ecf39af53c1bb826823d",
    "blockNumber": 453475,
    "epoch": 5543,
    "lastCommitBitmap": "ffffffffffffffff0f4000",
    "lastCommitSig": "701bad22a95b7ee937446c3f614755d1729f19b5976f1230af6de65fd7ecc0d8b95795396a55d78994b5a8ecaed77d028721f76a58e9919ab01f4aba36a6f3a3dda3aaf39b313e5d623e73ca83d71fc1631ae964e1747826662652be85fada18",
    "leader": "one18vn4hpu8jpu8p9pql59m7p0x8dqrpsw0jzav9u",
    "shardID": 2,
    "timestamp": "2019-12-11 12:22:26 +0000 UTC",
    "unixtime": 1576066946,
    "viewID": 453508
  }
}
```
{% endtab %}

{% tab title="Shard 3" %}
```text
./hmy blockchain latest-header --node=https://api.s3.t.hmny.io

{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0xd5775e720a9bcc5a88fd13aac27d72365f4724d6a513ecf39af53c1bb826823d",
    "blockNumber": 453475,
    "epoch": 5543,
    "lastCommitBitmap": "ffffffffffffffff0f4000",
    "lastCommitSig": "701bad22a95b7ee937446c3f614755d1729f19b5976f1230af6de65fd7ecc0d8b95795396a55d78994b5a8ecaed77d028721f76a58e9919ab01f4aba36a6f3a3dda3aaf39b313e5d623e73ca83d71fc1631ae964e1747826662652be85fada18",
    "leader": "one188345hbsgdsgstw6eenjgxsgusgs",
    "shardID": 2,
    "timestamp": "2019-12-11 12:22:26 +0000 UTC",
    "unixtime": 1576066946,
    "viewID": 453508
  }
}
```
{% endtab %}
{% endtabs %}

### block-by-number

{% hint style="info" %}
Note the block-number provided must be in hex with a 0x prefix.

For example if you call latest-header and get a result of `10657` you convert this to hex which is `29A1` and then use the value `0x29A1` for block-number. This can be done using

`printf '0x%x\n' 10617 #0X29a1`
{% endhint %}

#### Using the Binary:

```text
./hmy --node=https://api.s0.os.hmny.io blockchain block-by-number <<block-number>>
```

#### Using the Shell Wrapper:

```text
./hmy.sh --node=https://api.s0.os.hmny.io blockchain block-by-number <<block-number>>
```

#### Example:

```text
./hmy --node=https://api.s0.os.hmny.io blockchain block-by-number 0x29A1

{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "difficulty": 0,
    "extraData": "0x",
    "gasLimit": "0x4c4b400",
    "gasUsed": "0x0",
    "hash": "0x5cb6e0752530cef5e25c52539feca22b8ad197cca60c04cf06f4ee05d6537096",
    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "miner": "0x3f6e680ec5456f540a833e77df4c8ed20a20f274",
    "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "nonce": 0,
    "number": "0x29a1",
    "parentHash": "0x30d28fb69701f8348e0cd6a7abbacceb4286009fc43827dc243e79508da057d7",
    "receiptsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
    "size": "0x50c",
    "stakingTransactions": [],
    "stateRoot": "0x096fac171e818e54e611d3543fd43b1929a4468d17dcb8766d18eaf1e426749c",
    "timestamp": "0x5e755a56",
    "transactions": [],
    "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
    "uncles": []
  }
}
```

