---
description: hmy_getAllValidatorInformationByBlockNumber
---

# hmy\_getAllValidatorInformationByBlockNumber

Get staking validator information snapshot for all validators by blocknum.

## Parameters

1. `Number` - page num (default use 0)
2. `Number` - block number

## Returns

Array of:

* `current-epoch-signing-percent`
  * `current-epoch-signed` - `Number` - epoch when last block was signed by validator
  * `current-epoch-to-sign` - `Number` - current epoch
  * `percentage` - `Float` - percentage of blocks signed
* `current-epoch-voting-power` - `Array of`
  * `effective-stake` - `Float `- effective validator stake
  * `shard-id` - `Number` - shard id
  * `voting-power-adjusted` - `Float` - voting power adjusted
  * `voting-power-raw` - `Float` - voting power
* validator
  * `availability:`
    * `num-of-blocks-to-sign` - `Number` - big.Int number of blocks validator should have signed in active mode
    * `num-blocks-signed` - `Number` - big.Int number of blocks validator actually signed
  * `address` - `String` - ECSDA validator address
  * `bls-public-keys` - `[]String` - array of validator bls public keys
  * `last-epoch-in-committee` - `Number` - big.Int last epoch in committee
  * `min-self-delegation` - `Number` - big.Int min self delegation
    * `max-total-delegation` - `Number` - big.Int max total delegated to this validator
  * `active` - `Bool` - is valdiator currently active
  * `rate` - `Float` - validator current commission rate
  * `max-rate` - `Float` - max validator commission rate
  * `max-change-rate` - `Float` - max validator commission rate change
  * `update-height`  - `Number` - big.Int last commission update block height
  * `name` - `String` - validator name
  * `identity` - `String` - validator text kyc identity
  * `website` - `String` - validator website
  * `security-contact` - `String` - validator security contact
  * `details` - `String` - additional info
  * `creation-height` - `Number` - big.Int block height when validator was created
  * `banned` - `Bool` - is validator banned
  * `Delegations:`
    * array of validator delegations, check out delegations format in hmy\_getDelegationsBy...



**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getAllValidatorInformationByBlockNumber",
    "params":[0, 7376688],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
      {
        "id": "0",
        "jsonrpc": "2.0",
        "result": {
          "current-epoch-signing-percent": {
            "current-epoch-signed": 0,
            "current-epoch-to-sign": 5,
            "percentage": "0.000000000000000000"
          },
          "current-epoch-voting-power": [
            {
              "effective-stake": "25415000000000000000.000000000000000000",
              "shard-id": 2,
              "voting-power-adjusted": "0.320000000000000000",
              "voting-power-raw": "1.000000000000000000"
            }
          ],
          "validator": {
            "active": false,
            "address": "one14438psd5vrjes7qm97jrj3t0s5l4qff5j5cn4h",
            "availability": {
              "num-blocks-signed": 0,
              "num-blocks-to-sign": 75
            },
            "banned": false,
            "bls-public-keys": [
              "67336532c04545afc5c1c979f58b5c301af406eaa0f4c900dcd3004189936c7213ee126d9591026f65248e5f25278f02"
            ],
            "creation-height": 240,
            "delegations": [
              {
                "amount": 3.46e+19,
                "delegator-address": "one14438psd5vrjes7qm97jrj3t0s5l4qff5j5cn4h",
                "reward": 0,
                "undelegations": []
              },
              {
                "amount": 1.5e+18,
                "delegator-address": "one1nqevvacj3y5ltuef05my4scwy5wuqteur72jk5",
                "reward": 0,
                "undelegations": []
              }
            ],
            "details": "none",
            "identity": "test_account2",
            "last-epoch-in-committee": 4,
            "max-change-rate": "0.052212761523253600",
            "max-rate": "0.179184469782137200",
            "max-total-delegation": 8e+19,
            "min-self-delegation": 3.2e+18,
            "name": "_Test_key_validator2",
            "rate": "0.127983520183826780",
            "security-contact": "Edgar-VDM",
            "update-height": 240,
            "website": "harmony.one"
          }
        }
      }
    ]
}
```
