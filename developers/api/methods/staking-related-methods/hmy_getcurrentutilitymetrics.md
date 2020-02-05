---
description: hmy_getCurrentUtilityMetrics
---

# hmy\_getCurrentUtilityMetrics

#### Description

Works only for shard 0 \(beacon chain\).

#### Returns

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getCurrentUtilityMetrics",
    "params":[],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "accumulator": 0,
        "staked-percentage": "0.000000000000000000",
        "deviation": "0.350000000000000000",
        "adjustment": "14000000000000000000.000000000000000000"
    }
}
```

