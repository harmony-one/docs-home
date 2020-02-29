---
description: hmy_getDelegationsByDelegatorAndValidator
---

# hmy\_getDelegationsByDelegatorAndValidator

#### Parameters

1. `String` - delegator bech32 address.
2. `String` - validator bech32 address.

#### Returns

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

```text

   // ECDSA address of the validator
   Address common.Address `json:"address"`
   // The BLS public key of the validator for consensus
   SlotPubKeys []shard.BlsPublicKey `json:"bls-public-keys"`
   // The number of the last epoch this validator is
   // selected in committee (0 means never selected)
   LastEpochInCommittee *big.Int `json:"last-epoch-in-committee"`
   // validator's self declared minimum self delegation
   MinSelfDelegation *big.Int `json:"min-self-delegation"`
   // maximum total delegation allowed
   MaxTotalDelegation *big.Int `json:"max-total-delegation"`
   // Is the validator active in participating
   // committee selection process or not
   Active bool `json:"active"`
   // commission parameters
   Commission
   // description for the validator
   Description
   // CreationHeight is the height of creation
   CreationHeight *big.Int `json:"creation-height"`
   // Banned records whether this validator is banned
   // from the network because they double-signed
   Banned bool `json:"banned"`
```



**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getDelegationsByDelegatorAndValidator",
    "params":[
      "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7",
      "one129r9pj3sk0re76f7zs3qz92rggmdgjhtwge62k"
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

