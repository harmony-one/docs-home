---
description: GetStorageAt
---

# hmy\_getStorageAt

\*\*\*\*

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getStorageAt",
    "params":[
    "0xD7Ff41CA29306122185A07d04293DdB35F24Cf2d", "0", "latest"],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x0000000000000000000000000000000000000000000000000000000000000000"
}
```

