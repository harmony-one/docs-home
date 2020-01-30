---
description: hmy_getLogs
---

# hmy\_getLogs

Get harmony logs for smart contracts or transactions

#### Parameters

1. `Object` - The filter options:

* `fromBlock`: `QUANTITY|TAG` - \(optional, default: `"latest"`\) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
* `toBlock`: `QUANTITY|TAG` - \(optional, default: `"latest"`\) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
* `address`: `DATA|Array`, 20 Bytes - \(optional\) Contract address or a list of addresses from which logs should originate.
* `topics`: `Array of DATA`, - \(optional\) Array of 32 Bytes `DATA` topics. Topics are order-dependent. Each topic can also be an array of DATA with "or" options.
* `blockhash`:  `DATA`, 32 Bytes - \(optional\) , `blockHash` is a new filter option which restricts the logs returned to the single block with the 32-byte hash `blockHash`. Using `blockHash` is equivalent to `fromBlock` = `toBlock` = the block number with hash `blockHash`. If `blockHash` is present in the filter criteria, then neither `fromBlock` nor `toBlock` are allowed.

#### Returns

For filters created with `hmy_newBlockFilter` the return are block hashes \(`DATA`, 32 Bytes\), e.g. `["0x3454645634534..."]`.

For filters created with `hmy_newPendingTransactionFilter` the return are transaction hashes \(`DATA`, 32 Bytes\), e.g. `["0x6345343454645..."]`.

For filters created with `hmy_newFilter` logs are objects with following params:

* `removed`: `TAG` - `true` when the log was removed, due to a chain reorganization. `false` if its a valid log.
* `logIndex`: `QUANTITY` - integer of the log index position in the block. `null` when its pending log.
* `transactionIndex`: `QUANTITY` - integer of the transactions index position log was created from. `null` when its pending log.
* `transactionHash`: `DATA`, 32 Bytes - hash of the transactions this log was created from. `null` when its pending log.
* `blockHash`: `DATA`, 32 Bytes - hash of the block where this log was in. `null` when its pending. `null` when its pending log.
* `blockNumber`: `QUANTITY` - the block number where this log was in. `null` when its pending. `null` when its pending log.
* `address`: `DATA`, 20 Bytes - address from which this log originated.
* `data`: `DATA` - contains the non-indexed arguments of the log.
* `topics`: `Array of DATA` - Array of 0 to 4 32 Bytes `DATA` of indexed log arguments. \(In _solidity_: The first topic is the _hash_ of the signature of the event \(e.g. `Deposit(address,bytes32,uint256)`\), except you declared the event with the `anonymous` specifier.\)

**Sample Curl Request**

```bash
curl -X POST --data 
'{
    "jsonrpc":"2.0",
    "method":"hmy_getLogs",
    "params":[
        {"topics":
            ["0x000000000000000000000000a94f5374fce5edbc8e2a8697c15331677e6ebf0b"]
        }
    ],
    "id":74
}'
```

**Sample Curl Response**

```javascript
{
  "id":1,
  "jsonrpc":"2.0",
  "result": [{
    "logIndex": "0x1", // 1
    "blockNumber":"0x1b4", // 436
    "blockHash": "0x8216c5785ac562ff41e2dcfdf5785ac562ff41e2dcfdf829c5a142f1fccd7d",
    "transactionHash":  "0xdf829c5a142f1fccd7d8216c5785ac562ff41e2dcfdf5785ac562ff41e2dcf",
    "transactionIndex": "0x0", // 0
    "address": "0x16c5785ac562ff41e2dcfdf829c5a142f1fccd7d",
    "data":"0x0000000000000000000000000000000000000000000000000000000000000000",
    "topics": ["0x59ebeb90bc63057b6515673c3ecf9438e5058bca0f92585014eced636878c9a5"]
    },{
      ...
    }]
}
```

## 

