---
description: hmy_getStakingTransactionByHash
---

# hmy\_getStakingTransactionByHash

Get staking transaction by its hash.

## API v1

### Parameters

1. `String` - The staking transaction hash.

### Returns

* `hash` - `String`: Hash of the transaction.
* `nonce` - `Number`: The number of transactions made by the sender prior to this one.
* `blockHash` - `String`: Hash of the block where this transaction was in. `null` when its pending.
* `blockNumber` - `Number`: Block number where this transaction was in. `null` when its pending.
* `transactionIndex` - `Number`: Integer of the transactions index position in the block. `null` when its pending.
* `timestamp` - `Number`: transaction timestamp&#x20;
* `from` - `String`: Address of the sender.
* `value` - `String`: Value transferred in ATTO.
* `gasPrice` - `String`: Gas price provided by the sender.
* `gas` - `Number`: Gas provided by the sender.
* `v` - `String`: signature V
* `r` - `String`: signature R
* `s` - ~~`String`~~: signature S
* `type` - `String`: staking transaction type ("CreateValidator", "EditValidator", "CollectRewards", "Undelegate", "Delegate")
* `msg` - `StakingMsg:`
  * `CreateValidator:`
    * `validatorAddress` - `String:` validator address
    * `name` - `String:` validator name
    * `commissionRate` - `Number`: validator commission rate
    * `maxCommissionRate` - `Number`: validator commission rate
    * `maxChangeRate` - `Number`: validator max commission rate change
    * `minSelfDelegation` - `Number`: min how much validator self delegates
    * `maxTotalDelegation` - `Number`: max total delegation to validator
    * `amount` - `Number`: stake amount for validator
    * `website` - `String`: validator website
    * `identity` - `String`: validator kyc identity
    * `securityContact` - `String`: validator security contact
    * `details` - `String`: additional validator info
    * `slotPubKeys` - `[]String`: validator bls pub keys
  * `EditValidator:`
    * `validatorAddress` - `String:` validator address
    * `name` - `String`: validator name
    * `commissionRate` - `Number`: validator commission rate
    * `minSelfDelegation` - `Number`: min how much validator self delegates
    * `maxTotalDelegation` - `Number`: max total delegation to validator
    * `website` - `String`: validator website
    * `identity` - `String`: validator kyc identity
    * `securityContact` - `String`: validator security contact
    * `details` - `String`: additional validator info
    * `slotPubKeyToAdd` - `String`: validator bls pub key to add
    * `slotPubKeyToRemove` - `String`: validator bls pub key to remove
  * `CollectRewards:`
    * `delegatorAddress` - `String`: address to send rewards
  * `Delegate:`
    * `delegatorAddress` - `String:` delegation delegator address
    * `validatorAddress` - `String:` delegation validator address
    * `amount` - `Number`: big.Int amount for delegation to validator
  * `Undelegate:`
    * `delegatorAddress` - `String`: undelegation delegator address
    * `validatorAddress` - `String`: undelegation validator address
    * `amount` - `Number`: big.Int amount for undelegation to delegator

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getStakingTransactionByHash",
    "params":[
      "0x1dff358dad4d0fc95b11acc9826b190d8b7971ac26b3f7ebdee83c10cafaf86f"
    ],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": null
}
```

## API v2

### Parameters

1. `String`- The staking transaction hash.

### Returns

* `hash` - `String`: Hash of the transaction.
* `nonce` - `Number`: The number of transactions made by the sender prior to this one.
* `blockHash` - `String`: Hash of the block where this transaction was in. `null` when its pending.
* `blockNumber` - `Number`: Block number where this transaction was in. `null` when its pending.
* `transactionIndex` - `Number`: Integer of the transactions index position in the block. `null` when its pending.
* `timestamp` - `Number`: transaction timestamp&#x20;
* `from` - `String`: Address of the sender.
* `value` - `String`: Value transferred in ATTO.
* `gasPrice` - `String`: Gas price provided by the sender.
* `gas` - `Number`: Gas provided by the sender.
* `v` - `String`: signature V
* `r` - `String`: signature R
* `s` - ~~`String`~~: signature S
* `type` - `String`: staking transaction type ("CreateValidator", "EditValidator", "CollectRewards", "Undelegate", "Delegate")
* `msg` - `StakingMsg:`
  * `CreateValidator:`
    * `validatorAddress` - `String:` validator address
    * `name` - `String:` validator name
    * `commissionRate` - `Number`: validator commission rate
    * `maxCommissionRate` - `Number`: validator commission rate
    * `maxChangeRate` - `Number`: validator max commission rate change
    * `minSelfDelegation` - `Number`: min how much validator self delegates
    * `maxTotalDelegation` - `Number`: max total delegation to validator
    * `amount` - `Number`: stake amount for validator
    * `website` - `String`: validator website
    * `identity` - `String`: validator kyc identity
    * `securityContact` - `String`: validator security contact
    * `details` - `String`: additional validator info
    * `slotPubKeys` - `[]String`: validator bls pub keys
  * `EditValidator:`
    * `validatorAddress` - `String:` validator address
    * `name` - `String`: validator name
    * `commissionRate` - `Number`: validator commission rate
    * `minSelfDelegation` - `Number`: min how much validator self delegates
    * `maxTotalDelegation` - `Number`: max total delegation to validator
    * `website` - `String`: validator website
    * `identity` - `String`: validator kyc identity
    * `securityContact` - `String`: validator security contact
    * `details` - `String`: additional validator info
    * `slotPubKeyToAdd` - `String`: validator bls pub key to add
    * `slotPubKeyToRemove` - `String`: validator bls pub key to remove
  * `CollectRewards:`
    * `delegatorAddress` - `String`: address to send rewards
  * `Delegate:`
    * `delegatorAddress` - `String:` delegation delegator address
    * `validatorAddress` - `String:` delegation validator address
    * `amount` - `Number`: big.Int amount for delegation to validator
  * `Undelegate:`
    * `delegatorAddress` - `String`: undelegation delegator address
    * `validatorAddress` - `String`: undelegation validator address
    * `amount` - `Number`: big.Int amount for undelegation to delegator

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmyv2_getStakingTransactionByHash",
    "params":[
       "0x1dff358dad4d0fc95b11acc9826b190d8b7971ac26b3f7ebdee83c10cafaf86f"
    ],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": null
}
```
