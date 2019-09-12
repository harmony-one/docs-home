---
description: GetTransactionByHash
---

# hmy\_getTransactionByHash

Get a transaction by its hash.

## Parameters

1. `String` - The transaction hash.

## Returns

* `hash` - `String`: Hash of the transaction.
* `nonce` - `Number`: The number of transactions made by the sender prior to this one.
* `blockHash` - `String`: Hash of the block where this transaction was in. `null` when its pending.
* `blockNumber` - `Number`: Block number where this transaction was in. `null` when its pending.
* `transactionIndex` - `Number`: Integer of the transactions index position in the block. `null` when its pending.
* `from` - `String`: Address of the sender.
* `to` - `String`: Address of the receiver.
* `value` - `String`: Value transferred in ATTO.
* `gasPrice` - `String`: Gas price provided by the sender.
* `gas` - `Number`: Gas provided by the sender.
* `input` - `String`: The data sent along with the transaction.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getTransactionByHash",
    "params":[
    "0x1dff358dad4d0fc95b11acc9826b190d8b7971ac26b3f7ebdee83c10cafaf86f"],
    "id":1
}'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockHash": "0xd6db4b8e899b25c584384a1369082c79f1a4a4d1c28a49d082507c4bce2a389e",
        "blockNumber": "0x14",
        "from": "0x806171f95c5a74371a19e8a312c9e5cb4e1d24f6",
        "gas": "0x5208",
        "gasPrice": "0x0",
        "hash": "0x1dff358dad4d0fc95b11acc9826b190d8b7971ac26b3f7ebdee83c10cafaf86f",
        "input": "0x",
        "nonce": "0x0",
        "to": "0xd7ff41ca29306122185a07d04293ddb35f24cf2d",
        "transactionIndex": "0x0",
        "value": "0x1158e460913d00000",
        "v": "0x1c",
        "r": "0x4ee6562ebdc9cbb3ed0ce2c57ededd95573cea1749e79e8fdf8f98e8788dd944",
        "s": "0x30194af0e6b01a8b3aefb2ad01c896a20aa20a9ebb7a67ae9bb21783f75f9fd"
    }
}
```

