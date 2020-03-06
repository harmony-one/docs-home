# hmy\_getStakingNetworkInfo

Get global staking info.

## Returns

* `total-staking` - `Number` - big.Int total staking by validators
* `circulating-supply` - `Float` - current circulating supply
* `total-supply` - `Number` - total ONE supply \(12600000000\)
* `median-raw-stake` - `Float` - median raw validators stake
* `epoch-last-block` - `Number` - previous epoch last block

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getStakingNetworkInfo",
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
        "total-supply": "12600000000.000000000000000000",
        "circulating-supply": "5098814411.764701600000000000",
        "epoch-last-block": 134,
        "total-staking": 0,
        "median-raw-stake": 0
    }
}
```

