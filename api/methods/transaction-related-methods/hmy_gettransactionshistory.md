# hmy\_getTransactionsHistory

## Description

hmy\_getTransactionsHistory get transactions history for an address

## Parameters

* `String` - one address \("one1..."\)
* `txHistoryArgs` - json args
  * `txType` - `String` : optional, Received or Sent, shows all transactions by default
  * `fullTx` - `Bool` :  optional, shows full transaction or just its hash, default is false
  * `pageSize` - `Number` : optional, pagination page size, how much tx to show in single page, default is 100
  * `pageIndex` - `Number` : optional, pagination which page to show, default is 0
  * `txType` - `String`: optional, "ALL", "RECEIVED", "SENT", default is "ALL"
  * `order` - `String`: optional, "ASC", "DESC", default is "ASC", order by timestamp

## Returns

* `Array` - either returns list of transactions
  * `hash` - `String`: Hash of the transaction.
  * `nonce` - `Number`: The number of transactions made by the sender prior to this one.
  * `blockHash` - `String`: Hash of the block where this transaction was in. `null` when it's pending.
  * `blockNumber` - `Number`: Block number where this transaction was in. `null` when it's pending.
  * `transactionIndex` - `Number`: Integer of the transaction's index position in the block. `null` when its pending.
  * `from` - `String`: Address of the sender.
  * `to` - `String`: Address of the receiver.
  * `value` - `String`: Value transferred in ATTO.
  * `gasPrice` - `String`: Gas price provided by the sender.
  * `gas` - `Number`: Gas provided by the sender.
  * `input` - `String`: The data sent along with the transaction.
* `Array` of `String` - or list of transactions hashes

**Sample Curl Request 0**

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_getTransactionsHistory",
    "params": [{
        "address": "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7",
        "pageIndex": 0,
        "pageSize": 1000,
        "fullTx": true,
        "txType": "ALL",
        "order": "ASC"
    }],
    "id": 1
}'
```

**Sample Curl Response 0**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "transactions": [
            {
                "blockHash": "0x0bde901cd3599aa082482777fd0a7fed3f02b7b5a9096b7ea7b2fcb8addaa05d",
                "blockNumber": "0x12",
                "from": "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7",
                "gas": "0x5208",
                "gasPrice": "0x3b9aca00",
                "hash": "0x230798fe22abff459b004675bf827a4089326a296fa4165d0c2ad27688e03e0c",
                "input": "0x",
                "nonce": "0x0",
                "to": "one129r9pj3sk0re76f7zs3qz92rggmdgjhtwge62k",
                "transactionIndex": "0x1",
                "value": "0x16345785d8a0000",
                "shardID": 0,
                "toShardID": 0,
                "v": "0x27",
                "r": "0x57766aa1304e97f8b71a9fa54a61b61ce8ef9ad177fcb337dd81827aad184327",
                "s": "0x3b3e5767899e8af5e75d62243a725371f08705b91e2305459e6fd8e8d2646651"
            }
        ]
    }
}
```

**Sample Curl Request 1**

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_getTransactionsHistory",
    "params": [{
        "address": "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7",
        "pageIndex": 0,
        "pageSize": 1000,
        "fullTx": false,
        "txType": "ALL",
        "order": "ASC"
    }],
    "id": 1
}'
```

**Sample Curl Response 1**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "transactions": [
            "0x230798fe22abff459b004675bf827a4089326a296fa4165d0c2ad27688e03e0c"
        ]
    }
}
```

