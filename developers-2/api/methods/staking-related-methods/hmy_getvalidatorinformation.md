---
description: hmy_getValidatorInformation
---

# hmy\_getValidatorInformation

Get staking validator information.

## Parameters

1. `String` - validator bech32 address.

## Returns

* `address` - `String` - ECSDA validator address
* `bls-public-keys` - `[]String` - array of validator bls public keys
* `last-epoch-in-committee` - `Number` - big.Int last epoch in committee
* `min-self-delegation` - `Number` - big.Int min self delegation
* `max-total-delegation` - `Number` - big.Int max total delegated to this validator
* `active` - `Bool` - is valdiator currently active
* `commission:`
  * `rate` - `Float` - validator current commission rate
  * `max-rate` - `Float` - max validator commission rate
  * `max-change-rate` - `Float` - max validator commission rate change
  * `update-height`  - `Number` - big.Int last commission update block height
* `description:`
  * `name` - `String` - validator name
  * `identity` - `String` - validator text kyc identity
  * `website` - `String` - validator website
  * `security-contact` - `String` - validator security contact
  * `details` - `String` - additional info
* `creation-height` - `Number` - big.Int block height when validator was created
* `banned` - `Bool` - is validator banned
* `Delegations:`
  * array of validator delegations, check out delegations format in hmy\_getDelegationsBy...
* `Counters:`
  * `num-of-blocks-to-sign` - `Number` - big.Int number of blocks validator should have signed in active mode
  * `num-blocks-signed` - `Number` - big.Int number of blocks validator actually signed

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getValidatorInformation",
    "params":[
      "one1tnnncpjdqdjyk7y4d9gaxrg9qk927ueqptmptz"
    ],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "one-address": "one1tnnncpjdqdjyk7y4d9gaxrg9qk927ueqptmptz",
        "bls-public-keys": [
            "6706f27d2a28d167f85d54c7fd8ee1f6177cde266f0e1669e0e90d8cb377937135fc5daa0950f339c6e9b0177f326c84"
        ],
        "min-self-delegation": "1000000000000000000",
        "max-total-delegation": "200000000000000000000000",
        "active": true,
        "commission": {
            "rate": "0.100000000000000000",
            "max-rate": "0.500000000000000000",
            "max-change-rate": "0.100000000000000000"
        },
        "description": {
            "name": "R",
            "identity": "J",
            "website": "harmony.one",
            "security_contact": "J",
            "details": "Shard0Validator"
        },
        "creation-height": 347
    }
}
```

