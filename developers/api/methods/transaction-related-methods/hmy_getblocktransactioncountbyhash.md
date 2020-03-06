---
description: GetBlockTransactionCount
---

# hmy\_getBlockTransactionCountByHash

Get the number of transactions in a block by the block's hash.

## API v1

### Parameters

`String` - The block hash.

### Returns

* `Number` - The number of transactions in the given block.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getBlockTransactionCountByHash",
    "params":["0x660fe701f580ffebfcfb4af1836c9929c1fd0014d8d79d60749fecf52df7a90d"],
    "id":1
}' -H "Content-Type:application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x0"
}
```

## API v2

### Parameters

1. `String` - The block hash.

### Returns

* `Number` - The number of transactions in the given block.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmyv2_getBlockTransactionCountByHash",
    "params":["0x660fe701f580ffebfcfb4af1836c9929c1fd0014d8d79d60749fecf52df7a90d"],
    "id":1
}' -H "Content-Type:application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": 1
}
```

