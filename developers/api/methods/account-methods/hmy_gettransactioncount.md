---
description: GetTransactionCount
---

# hmy\_getTransactionCount

Given an account address, returns the number of transactions the account has made.

## API v1

### Parameters

1. `String` - Account address
2. `String` - Block number to query for transaction count. Usually `latest`, which uses the most recent block.

### Returns

* `String` - Number of transactions the account has made.

### Sample Curl Request

```bash
curl -d '{
  "jsonrpc": "2.0",
  "method": "hmy_getTransactionCount",
  "params": [
    "one1rgl8538wyygp6ltyl0efkrm0rlpftaertskl80",
    "latest"
  ],
  "id": 1
}' -H "Content-Type:application/json" -X POST "http://s0.b.hmny.io:9500"
```

### Sample Curl Response

```javascript
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x9"
}
```

## API v2

### Parameters

1. `String` - Account address
2. `Number` - Block number to query for transaction count.

### Returns

* `Number` - Number of transactions the account has made.

### Sample Curl Request

```bash
curl -d '{
  "jsonrpc": "2.0",
  "method": "hmyv2_getTransactionCount",
  "params": [
    "one1rgl8538wyygp6ltyl0efkrm0rlpftaertskl80",
    1
  ],
  "id": 1
}' -H "Content-Type:application/json" -X POST "http://s0.b.hmny.io:9500"
```

### Sample Curl Response

```javascript
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 9
}
```
