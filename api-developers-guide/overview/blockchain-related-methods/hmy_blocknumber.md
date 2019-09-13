---
description: BlockNumber
---

# hmy\_blockNumber

Get number of the most recent block.

#### Returns

* `Number` - Index of the most recent block in the chain.

**Sample Curl Request**

```bash
 curl -d '{
  "jsonrpc":"2.0",
  "method":"hmy_blockNumber",
  "params":[],
  "id":1
 }' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x4b0"
}
```

