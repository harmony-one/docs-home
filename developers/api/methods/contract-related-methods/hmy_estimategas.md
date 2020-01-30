---
description: hmy_estimateGas
---

# hmy\_estimateGas

Generates and returns an estimate of how much gas is necessary to allow the transaction to complete. The transaction will not be added to the blockchain.

**Parameters**

See hmy\_call parameters, expect that all properties are optional. If no gas limit is specified geth uses the block gas limit from the pending block as an upper bound. As a result the returned estimate might not be enough to executed the call/transaction when the amount of gas is higher than the pending block gas limit.

**Returns**

`QUANTITY` - the amount of gas used.

**Example**

```text
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"hmy_estimateGas","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x5208" // 21000
}
```

