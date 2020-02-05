---
description: hmy_getStakingTransactionByBlockNumberAndIndex
---

# hmy\_getStakingTransactionByBlockNumberAndIndex

Get staking transaction at an index from a given block, specified by number.

## API v1

### Parameters

1. `String` - The block's index in the chain.
2. `String` - The staking transactions index position.

### Returns

* `hash` - `String`: Hash of the staking transaction.
* `nonce` - `Number`: The number of transactions made by the sender prior to this one.
* `blockHash` - `String`: Hash of the block where this transaction was in. `null` when its pending.
* `blockNumber` - `Number`: Block number where this transaction was in. `null` when its pending.
* `transactionIndex` - `Number`: Integer of the transactions index position in the block. `null` when its pending.
* `from` - `String`: Address of the sender.
* `to` - `String`: Address of the receiver. `null` when its a contract creation transaction.
* `value` - `String`: Value transferred in ATTO.
* `gasPrice` - `String`: Gas price provided by the sender.
* `gas` - `Number`: Gas provided by the sender.
* `input` - `String`: The data sent along with the transaction.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getStakingTransactionByBlockNumberAndIndex",
    "params":[
        "0x4",
        "0x0"
    ],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockHash": "0x428ead93e632d5255ea3d1fb61b02ab8493cf562a398af2159c33ecd53c62c16",
        "blockNumber": "0x4",
        "from": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016",
        "gas": "0x5208",
        "gasPrice": "0x0",
        "hash": "0xa7bb2c7cbfe4f5d6cf061aacd9d0dce7660d1f82da63dd7c76d9e856c1dc0278",
        "input": "0x",
        "nonce": "0x0",
        "to": "0x3aea49553ce2e478f1c0c5acc304a84f5f4d1f98",
        "transactionIndex": "0x0",
        "value": "0xde0b6b3a7640000",
        "v": "0x1b",
        "r": "0x3cb6eedb11cad81f1ab52d72f46dcea0b3d7f46beaf40e83660b165546db5fc6",
        "s": "0x1bc4b99089ab7d3ec17eae9d8a366feac87f9a76dd3ae031abfb86359b020551"
    }
}
```

## API v2

### Parameters

1. `Number`- The block's index in the chain.
2. `Number` - The transactions index position.

### Returns

* `hash` - `String`: Hash of the transaction.
* `nonce` - `Number`: The number of transactions made by the sender prior to this one.
* `blockHash` - `String`: Hash of the block where this transaction was in. `null` when its pending.
* `blockNumber` - `Number`: Block number where this transaction was in. `null` when its pending.
* `transactionIndex` - `Number`: Integer of the transactions index position in the block. `null` when its pending.
* `from` - `String`: Address of the sender.
* `to` - `String`: Address of the receiver. `null` when its a contract creation transaction.
* `value` - `Number`: Value transferred in ATTO.
* `gasPrice` - `Number`: Gas price provided by the sender.
* `gas` - `Number`: Gas provided by the sender.
* `input` - `String`: The data sent along with the transaction.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmyv2_getStakingTransactionByBlockNumberAndIndex",
    "params":[
        4,
        0
    ],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockHash": "0x542ed61c1ed9e33592ef1b71324eab0b4535b5e66616cae60dc1ac5619a9c9d3",
        "blockNumber": 37,
        "from": "one1spshr72utf6rwxseaz339j09ed8p6f8ke370zj",
        "timestamp": 1580418556,
        "gas": 21000,
        "gasPrice": 1000000000,
        "hash": "0x4e58aff60b072d22d8fb023a20ee3f3ee543c406e4f44f0254ef9d9b0867b525",
        "input": "0x",
        "nonce": 8,
        "to": "one1r4zyyjqrulf935a479sgqlpa78kz7zlcg2jfen",
        "transactionIndex": 0,
        "value": 100000000000000000,
        "shardID": 0,
        "toShardID": 1,
        "v": "0x27",
        "r": "0xe207da6fa94432773f499a2f38b816b77f5034d4ec6d83684cd581739e8b528a",
        "s": "0xdfbe11c602c7956915ff1f01e240f0c65fd122fb798debaf040b551ed1bf6a6"
    }
}
```

