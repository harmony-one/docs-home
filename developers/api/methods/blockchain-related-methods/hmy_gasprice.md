---
description: GasPrice
---

# hmy_gasPrice

Returns the current gas price.

## API v1

**Returns**

* `String` - Number string of the current gas price.

**Sample Curl Request**

```bash
curl -d '{
  "jsonrpc":"2.0",
  "method":"hmy_gasPrice",
  "params":[],
  "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x1"
}
```

## API v2

**Returns**

* **String** - Decimal big.Int string of the current gas price.

**Sample Curl Request**

```bash
curl -d '{
  "jsonrpc":"2.0",
  "method":"hmyv2_gasPrice",
  "params":[],
  "id":1
}' -H 'Content-Type:application/json' localhost:9500
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "1"
}
```
