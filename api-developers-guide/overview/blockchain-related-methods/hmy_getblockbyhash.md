---
description: GetBlock
---

# hmy\_getBlockByHash

Get block by its hash.

#### Parameters

1. `common.Hash` - `String` The block hash. 
2. `bool` - `Boolean` - If `true`, the returned block will contain all transactions in the block.

#### Returns

`String` - The value in storage at the given position.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getBlockByHash",
    "params":[
    "0x660fe701f580ffebfcfb4af1836c9929c1fd0014d8d79d60749fecf52df7a90d", true],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
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
        "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
        "uncles": []
    }
}
```

