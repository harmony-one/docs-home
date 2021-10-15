---
description: hmy_getCurrentUtilityMetrics
---

# hmy_getCurrentUtilityMetrics

## Description

Works only for shard 0 (beacon chain).

## Returns

* `AccumulatorSnapshot` - `Number` - total staking
* `CurrentStakedPercentage` - `Float` - total staking percentage from circulating supply now
* `Deviation` - `Float` - deviation from average earned stake
* `Adjustment` - `Float` - adjustment

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
        "AccumulatorSnapshot": 0,
        "CurrentStakedPercentage": "0.000000000000000000",
        "Deviation": "0.350000000000000000",
        "Adjustment": "14000000000000000000.000000000000000000"
    }
}
```
