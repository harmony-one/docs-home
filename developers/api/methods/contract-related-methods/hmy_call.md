---
description: hmy_call
---

# hmy_call

Executes a new message call immediately without creating a transaction on the block chain.

**Parameters**

1. `Object` - The transaction call object
2. `from`: `DATA`, 20 Bytes - (optional) The address the transaction is sent from.
3. `to`: `DATA`, 20 Bytes - The address the transaction is directed to.
4. `gas`: `QUANTITY` - (optional) Integer of the gas provided for the transaction execution. eth_call consumes zero gas, but this parameter may be needed by some executions.
5. `gasPrice`: `QUANTITY` - (optional) Integer of the gasPrice used for each paid gas
6. `value`: `QUANTITY` - (optional) Integer of the value sent with this transaction
7. `data`: `DATA` - (optional) Hash of the method signature and encoded parameters.
8. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`

**Returns**

`DATA` - the return value of executed contract.

**Example**

```
// Request
curl -X POST "http://api.s0.b.hmny.io" --data '{
    "jsonrpc": "2.0",
    "method": "hmy_call",
    "params": [
        {
            "to": "0x08AE1abFE01aEA60a47663bCe0794eCCD5763c19"
        },
        "latest"
    ],
    "id": 1
}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x"
}
```
