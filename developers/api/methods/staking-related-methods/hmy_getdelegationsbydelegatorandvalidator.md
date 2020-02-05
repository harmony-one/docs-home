---
description: hmy_getDelegationsByDelegatorAndValidator
---

# hmy\_getDelegationsByDelegatorAndValidator

## Parameters

1. `String` - delegator bech32 address.
2. `String` - validator bech32 address.

## Returns

* `hash` - `String`: Hash of the transaction.
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
    "method":"hmy_getDelegationsByDelegatorAndValidator",
    "params":[
      "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7",
      "one129r9pj3sk0re76f7zs3qz92rggmdgjhtwge62k"
    ],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": []
}
```

