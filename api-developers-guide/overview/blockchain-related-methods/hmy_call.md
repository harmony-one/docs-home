---
description: Call
---

# hmy\_call

#### 

**Sample Curl Request**

```bash
curl -d '{
"jsonrpc":"2.0",
"method":"hmy_call",
"params":[
    {"to": "0x08AE1abFE01aEA60a47663bCe0794eCCD5763c19"},
    "latest"],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x"
}
```

