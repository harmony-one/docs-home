---
description: hmy_getDelegationsByDelegatorAndValidator
---

# hmy\_getDelegationsByDelegatorAndValidator

#### Parameters

1. `String` - delegator bech32 address.
2. `String` - validator bech32 address.

#### Returns

Array of:

* `validator_address` - `String` - validator bech32 address
* `delegator_address` - `String` - delegator bech32 address
* `amount` - `Number` - big.Int amount delegated to validator
* `reward` - `Number` - big.Int reward to validator for delegation
* `Undelegations` - `[]RPCUndelegation`:
  * `amount` - `Number` - big.Int amount returned to delegator
  * `reward` - `Number` - big.Int reward to validator

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

