---
description: hmy_latestHeader
---

# hmy\_latestHeader

## Parameters

None

## Returns

* `blockHash` - `String` - block hash
* `blockNumber` - `Number` - block number
* `shardID` - `Number` - shard id
* `leader` - `String` - leader address
* `viewID` - `Number` - current blockchain view of validators
* `epoch` - `Number` - blockchain epoch
* `timestamp` - `Date` - block generation timestamp date
* `unixtime` - `Number` - block generation time in Unix time
* `lastCommitSig` - `String` - BLS validators signature for the block
* `lastCommitBitmap` - `String` - last commit bitmap for block signers

## Sample Curl Request

```text
curl --location --request POST 'https://api.s0.b.hmny.io/' \
--header 'Content-Type: application/json' \
--data-raw '{
    "jsonrpc": "2.0",
    "method": "hmy_latestHeader",
    "params": [],
    "id": 1
}'
```

## Same Curl Response

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockHash": "0x4d5acd18f95ed1527a530c6427b518c4cf469912bfcc6df830efc36879c25170",
        "blockNumber": 80455,
        "shardID": 0,
        "leader": "one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw",
        "viewID": 80452,
        "epoch": 178,
        "timestamp": "2020-01-30 20:08:32 +0000 UTC",
        "unixtime": 1580414912,
        "lastCommitSig": "7e8cf8c683bf6433fb7da19ff0597e3b2fc631bc350b5fe805401cb3133cc466b991a0b91a898abb5bfb566f5607fb18064be8916d4e1d8217ad3880b7b7b0f79fdac4cd9dd8e9f82c438fb4e2025aee75beaeeb19b96ae0f63f6f9d63475289",
        "lastCommitBitmap": "ff03"
    }
}
```

