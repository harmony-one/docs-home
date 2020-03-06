---
description: hmy_getValidatorMetrics
---

# hmy\_getValidatorMetrics

## Parameters

1. `String` - validator bech32 address.

## Returns

* `NumJailed` - `Number` - big.Int number of times validator was banned due to downtime
* TotalEffectiveStake - Float - total validator effective stake from delegations
* `VotingPowerPerShard` - `[]VotePerShard`:
  * `shard-id` - `Number` - shard id
  * `voting-power` - `Float` - valdator voting power for this shard
* `BLSKeyPerShard` - `[]KeyPerShard:`
  * `shard-id` - `Number` - shard id
  * `keys` - `[]String` - validator bls keys for this shard

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getValidatorMetrics",
    "params":[
      "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"
    ],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": []
}
```

