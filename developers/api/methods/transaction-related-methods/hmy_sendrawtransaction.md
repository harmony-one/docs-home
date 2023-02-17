---
description: SendRawTransaction
---

# hmy\_sendRawTransaction

Send a raw transaction encoded in bytes.

## Parameters

* `String` - Transaction encoded in bytes.

## Returns

* `String` - Raw transaction's hash.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_sendRawTransaction",
    "params":[
      "0xf869808082520880809410a02a0a6e95a676ae23e2db04bea3d1b8b7ca2e880de0b6b3a7640000801ba0c8d0c5390086999b5b5a93373953c3c94b44dc8fd06d88a421a7c2461e9e4482a0730d7859d1e3109d499bcd75f00700729b9bc17b03940da4f84b6ea784f51eb1"
    ],
    "id":1
}' -H "Content-Type:application/json" -X POST "https://api.s0.b.hmny.io"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x1156a044c73f85d876780f3bd86d7b0665c2d1b6c8a1abaaaedc08c13968a598"
}
```
