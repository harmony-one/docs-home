---
description: GetBlockTransactionCount
---

# hmy\_getBlockTransactionCountByNumber

Get the number of transactions in a block by the block's index in the chain.

## Parameters

1. `Number` - The block number or hash.

## Returns

* `Number` - The number of transactions in the given block.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getBlockTransactionCountByNumber",
    "params":["0x66"],
    "id":1
}' -H "Content-Type:application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x0"
}
```

