---
description: hmy_getTotalSupply
---

# hmy\_getTotalSupply

Get total ONE supply

## Returns

* `Number` - total supply

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getTotalSupply",
    "params":[],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": 12600000000
}
```

