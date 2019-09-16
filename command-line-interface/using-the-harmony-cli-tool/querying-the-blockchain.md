---
description: Looking up information from the blockchain
---

# Querying the blockchain

## Querying the blockchain

The `hmy` provides several subcommands under the `blockchain` subcommand which let you query the blockchain.

## Targeting Specific Shards

As noted elsewhere in these docs, the Harmony blockchain is a _sharded_ blockchain, therefore some commands depend on which _shard_ you target. The shard you target when querying is controlled by the `--node` flag, for example:

```text
hash='0x599793f313ee17566f8d09728b9d043b8e26135ddce86beeee13f98767d452f7'
$ hmy --node="https://api.s1.b.hmny.io" blockchain transaction-receipt ${hash}
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": null
}
```

But invoking the same command on a different shard yields the transaction receipt:

```text
hash='0x599793f313ee17566f8d09728b9d043b8e26135ddce86beeee13f98767d452f7'
$ hmy --node="https://api.s0.b.hmny.io" blockchain transaction-receipt ${hash}
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

The only difference was _s1_ vs _s0_ in the URL given to the `--node` flag

`--node="https://api.s1.b.hmny.io"` vs `--node="https://api.s0.b.hmny.io"`

