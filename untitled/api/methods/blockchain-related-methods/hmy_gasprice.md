---
description: GasPrice
---

# hmy\_gasPrice

Returns the current gas price.

## Returns

* `String` - Number string of the current gas price.

**Sample Curl Request**

```bash
curl -d '{
  "jsonrpc":"2.0",
  "method":"hmy_gasPrice",
  "params":[],
  "id":1
}' -H 'Content-Type:application/json' localhost:9500
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x1"
}
```

