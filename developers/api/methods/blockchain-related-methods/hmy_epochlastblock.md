---
description: hmy_epochLastBlock
---

# hmy\_epochLastBlock

Epoch last block

**Parameters**

1. `Number` - epoch

## Returns

* `Number` - epoch last block height

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_epochLastBlock",
    "params":[],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "10"
}
```

