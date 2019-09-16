---
description: Syncing
---

# hmy\_syncing

Tests whether or not the node is syncing.

#### **Returns**

* `Object` - Whether or not the node is syncing. `false` when it isn't.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_syncing",
    "params":[],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": false
}
```

