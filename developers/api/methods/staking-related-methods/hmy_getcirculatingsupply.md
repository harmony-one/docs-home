---
description: hmy_getCirculatingSupply
---

# hmy_getCirculatingSupply

Get circulating ONE supply

## Returns

* `Number` - circulating supply

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getCirculatingSupply",
    "params":[],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "5098814411.764701600000000000"
}
```
