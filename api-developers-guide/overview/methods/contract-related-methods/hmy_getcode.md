---
description: GetCode
---

# hmy\_getCode

Get the code at a specific address.

## Parameters

1. `String` - The address to get the code from.
2. `String` - Block to query for information. Usually `latest`, which specifies the most recent block.
3. `Function` - \(optional\) Optional callback, returns an error object as first parameter and the result as second.

## Returns

* `String` - The data at given address `address`.

**Sample Curl Request**

```bash
curl -d '{
  "jsonrpc": "2.0",
  "method": "hmy_getCode",
  "params":[
    "0x08AE1abFE01aEA60a47663bCe0794eCCD5763c19",
    "latest"
  ],
  "id": 1
}' -H "Content-Type:application/json" -X POST "http://s0.b.hmny.io:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x608060405234801561001057600080fd5b506004361061004c5760003560e01c80630900f01014610051578063445df0ac146100955780638da5cb5b146100b3578063fdacd576146100fd575b600080fd5b6100936004803603602081101561006757600080fd5b81019080803573ffffffffffffffffffffffffffffffffffffffff16906020019092919050505061012b565b005b61009d6101f7565b6040518082815260200191505060405180910390f35b6100bb6101fd565b604051808273ffffffffffffffffffffffffffffffffffffffff1673ffffffffffffffffffffffffffffffffffffffff16815260200191505060405180910390f35b6101296004803603602081101561011357600080fd5b8101908080359060200190929190505050610222565b005b6000809054906101000a900473ffffffffffffffffffffffffffffffffffffffff1673ffffffffffffffffffffffffffffffffffffffff163373ffffffffffffffffffffffffffffffffffffffff1614156101f45760008190508073ffffffffffffffffffffffffffffffffffffffff1663fdacd5766001546040518263ffffffff1660e01b815260040180828152602001915050600060405180830381600087803b1580156101da57600080fd5b505af11580156101ee573d6000803e3d6000fd5b50505050505b50565b60015481565b6000809054906101000a900473ffffffffffffffffffffffffffffffffffffffff1681565b6000809054906101000a900473ffffffffffffffffffffffffffffffffffffffff1673ffffffffffffffffffffffffffffffffffffffff163373ffffffffffffffffffffffffffffffffffffffff16141561027f57806001819055505b5056fea165627a7a72305820792e3b111cfcc5a80ff42dc03094d528211b9c006cd3379069c81a942cea2e220029"
}
```

