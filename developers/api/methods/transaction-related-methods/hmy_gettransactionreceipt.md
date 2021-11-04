---
description: GetTransactionReceipt
---

# hmy\_getTransactionReceipt

Get transaction receipt from transaction hash.

## API v1

### Parameters

1. `String` - The transaction hash.

### Returns

* `blockHash` 32 Bytes - `String`: Hash of the block where this transaction was in.
* `blockNumber` - `Number`: Block number where this transaction was in.
* `transactionHash` 32 Bytes - `String`: Hash of the transaction.
* `transactionIndex`- `Number`: Integer of the transactions index position in the block.
* `from` - `String`: Address of the sender.
* `to` - `String`: Address of the receiver. `null` when its a contract creation transaction.
* `contractAddress` - `String`: The contract address created, if the transaction was a contract creation, otherwise `null`.
* `cumulativeGasUsed` - `Number`: The total amount of gas used when this transaction was executed in the block.
* `gasUsed`- `Number`: The amount of gas used by this specific transaction alone.
* `logs` - `Array`: Array of log objects, which this transaction generated.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getTransactionReceipt",
    "params":[
    "0x2fa714e40389cbbceda0f77e707035c0ec8aa940e8e10c0d445813177ea71e7d"],
    "id":1
}' -H "Content-Type:application/json" -X POST "http:s0.b.hmny.io"
```

**Sample Curl Response**

```javascript
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "blockHash": "0x6f45cf41eb252b8fc8482082992b516cbb42aa6f39002070e87d287f6007a29c",
    "blockNumber": "0x112e",
    "contractAddress": null,
    "cumulativeGasUsed": "0x5208",
    "from": "0x13e88a505dd804971410ac5538c504c376464227",
    "gasUsed": "0x5208",
    "logs": [],
    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "root": "0xf28ed9c84cc99e92ff61aa5c6076f697fcc4b288cd86c30048e1387f4e7928fa",
    "shardID": 0,
    "to": "0xe1217e2a4861dd5d50983dad32474bbfd6a7333f",
    "transactionHash": "0x2fa714e40389cbbceda0f77e707035c0ec8aa940e8e10c0d445813177ea71e7d",
    "transactionIndex": "0x0"
  }
}
```

## API v2

### Parameters

1. `String` - The transaction hash.

### Returns

* `blockHash` 32 Bytes - `String`: Hash of the block where this transaction was in.
* `blockNumber` - `Number`: Block number where this transaction was in.
* `transactionHash` 32 Bytes - `String`: Hash of the transaction.
* `transactionIndex`- `Number`: Integer of the transactions index position in the block.
* `from` - `String`: Address of the sender.
* `to` - `String`: Address of the receiver. `null` when its a contract creation transaction.
* `contractAddress` - `String`: The contract address created, if the transaction was a contract creation, otherwise `null`.
* `cumulativeGasUsed` - `Number`: The total amount of gas used when this transaction was executed in the block.
* `gasUsed`- `Number`: The amount of gas used by this specific transaction alone.
* `logs` - `Array`: Array of log objects, which this transaction generated.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmyv2_getTransactionReceipt",
    "params":[
    "0x2fa714e40389cbbceda0f77e707035c0ec8aa940e8e10c0d445813177ea71e7d"],
    "id":1
}' -H "Content-Type:application/json" -X POST "http:s0.b.hmny.io"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockHash": "0x86a26a6a2ed82c5bdfcbdde757243b35687363723c7d683f54b11c4f747a284b",
        "blockNumber": 17,
        "contractAddress": null,
        "cumulativeGasUsed": 21000,
        "from": "one1spshr72utf6rwxseaz339j09ed8p6f8ke370zj",
        "gasUsed": 21000,
        "logs": [],
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
        "shardID": 0,
        "status": 1,
        "to": "one1r4zyyjqrulf935a479sgqlpa78kz7zlcg2jfen",
        "transactionHash": "0xaab323cdbcba2c9c1be0c7b910bd6efdfbeba03323fad5c3794f1a527ec55ef0",
        "transactionIndex": 0
    }
}
```
