---
description: hmy_isLastBlock
---

# hmy\_isLastBlock

Is block epoch last block

**Parameters**

1. `Number` - block height

## Returns

* `Bool` - true if block epoch last block

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_isLastBlock",
    "params":["10"],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": true
}
```
