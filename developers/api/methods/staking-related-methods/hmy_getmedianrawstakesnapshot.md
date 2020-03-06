---
description: hmy_getMedianRawStakeSnapshot
---

# hmy\_getMedianRawStakeSnapshot

Returns active validators addresses list

## Returns

* `Number` - big.Int median raw stake of all validators

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getMedianRawStakeSnapshot",
    "params":[],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "1000000000000000"
}
```

