---
description: GetTransactionCount
---

# Not Implemented: hmy\_getTransactionCount

Get how many times a given transaction has been made.

## Parameters

1. `String` - The address to get the numbers of transactions from.
2. `Number|String` - Block to get query for balance; "latest" gives latest block.

**Returns**

* `Number` - The number of transactions sent from the given address.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getTransactionCount",
    "params":["one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw", "latest"],
    "id":1
}' -H 'Content-Type:application/json' 'http://localhost:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x3"
}
```

