---
description: hmy_getCXReceiptByHash
---

# hmy\_getCXReceiptByHash

## API v1

### Parameters

1. `String` - transactions hash for cx receipt

### Returns

* `blockHash` - `String` - block hash
* `blockNumber` - `Number` - block number
* `hash` - `String` - transaction hash
* `from` - `String` - from one address
* `to` - `String` - to one address
* `shardID` - `Number` - shard id from where transaction sent
* `toShardID` - `Number` - shard id to where transaction sent
* `value` - `Number` - transaction sent value

### Sample Curl Request

```text
curl --location --request POST 'https://api.s0.b.hmny.io/' \
--header 'Content-Type: application/json' \
--data-raw '{
    "jsonrpc": "2.0",
    "method": "hmy_getCXReceiptByHash",
    "params": [
        "0x6b106dc5619c86b6c0cb64b17e5c464e8008e08cf0f1bb0e3fa2657fb42daade"
    ],
    "id": 1
}'
```

### Sample Curl Response

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockHash": "0x864e39e8bd21bd983cd78231b5d14bb43a7f43d45bfa6111439956ce4be8bb5d",
        "blockNumber": "0x2b",
        "hash": "0x6b106dc5619c86b6c0cb64b17e5c464e8008e08cf0f1bb0e3fa2657fb42daade",
        "from": "one1uyshu2jgv8w465yc8kkny36thlt2wvel89tcmg",
        "to": "one1r4zyyjqrulf935a479sgqlpa78kz7zlcg2jfen",
        "shardID": 1,
        "toShardID": 0,
        "value": "0x16345785d8a0000"
    }
}
```

## API v2

### Parameters

1. `String` - transactions hash for cx receipt

### Returns

* `blockHash` - `String` - block hash
* `blockNumber` - `Number` - block number
* `hash` - `String` - transaction hash
* `from` - `String` - from one address
* `to` - `String` - to one address
* `shardID` - `Number` - shard id from where transaction sent
* `toShardID` - `Number` - shard id to where transaction sent
* `value` - `Number` - transaction sent value

### Sample Curl Request

```text
curl --location --request POST 'https://api.s0.b.hmny.io/' \
--header 'Content-Type: application/json' \
--data-raw '{
    "jsonrpc": "2.0",
    "method": "hmyv2_getCXReceiptByHash",
    "params": [
        "0xc6da1349d2c2fbb5724126fe9e462996f8f8b415275e411d39a72945d3cb05ef"
    ],
    "id": 1
}'
```

### Sample Curl Response

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockHash": "0x864e39e8bd21bd983cd78231b5d14bb43a7f43d45bfa6111439956ce4be8bb5d",
        "blockNumber": 43,
        "hash": "0x6b106dc5619c86b6c0cb64b17e5c464e8008e08cf0f1bb0e3fa2657fb42daade",
        "from": "one1uyshu2jgv8w465yc8kkny36thlt2wvel89tcmg",
        "to": "one1r4zyyjqrulf935a479sgqlpa78kz7zlcg2jfen",
        "shardID": 1,
        "toShardID": 0,
        "value": 100000000000000000
    }
}
```

