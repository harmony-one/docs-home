---
description: GetBlockByNumber
---

# hmy\_getBlockByNumber

Get block by its index in the blockchain.

## Parameters

1. `String` - The block number. 
2. `Boolean` - If `true`, the returned block will contain all transactions in the block.

## Returns

* `number` - `Number`: The block number. `null` when its pending block.
* `hash` 32 Bytes - `String`: Hash of the block. `null` when its pending block.
* `parentHash` 32 Bytes - `String`: Hash of the parent block.
* `nonce` 8 Bytes - `String`: Hash of the generated proof-of-work. `null` when its pending block.
* `logsBloom` 256 Bytes - `String`: The bloom filter for the logs of the block. `null` when its pending block.
* `transactionsRoot` 32 Bytes - `String`: The root of the transaction trie of the block
* `stateRoot` 32 Bytes - `String`: The root of the final state trie of the block.
* `miner` - `String`: The address of the beneficiary to whom the mining rewards were given.
* `difficulty` - `String`: Integer of the difficulty for this block.
* `extraData` - `String`: The “extra data” field of this block.
* `size` - `Number`: Integer the size of this block in bytes.
* `gasLimit` - `Number`: The maximum gas allowed in this block.
* `gasUsed` - `Number`: The total used gas by all transactions in this block.
* `timestamp` - `Number`: The unix timestamp for when the block was collated.
* `transactions` - `Array`: Array of transaction objects; absent if second parameter is `false`.
* `uncles` - `Array`: Array of uncle hashes.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getBlockByNumber",
    "params":[
    "0x66", true],
    "id":1
}' -H "Content-Type:application/json" -X POST "http://l0.b.hmny.io:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "difficulty": 0,
        "extraData": "0x",
        "gasLimit": "0x4f6e2a",
        "gasUsed": "0x0",
        "hash": "0x660fe701f580ffebfcfb4af1836c9929c1fd0014d8d79d60749fecf52df7a90d",
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
        "miner": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016",
        "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "nonce": 0,
        "number": "0x66",
        "parentHash": "0xcac989d8ba18e88ab245686e491a171d46b759e85290a3fc6df80553d2ac582f",
        "receiptsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
        "size": "0x25d",
        "stateRoot": "0x830ff6830857f88bdc56141449d0729a663c6413dc0dc909fc1f3715dd576cee",
        "timestamp": "0x5d570a3f",
        "transactions": [],
        "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
        "uncles": []
    }
}
```

