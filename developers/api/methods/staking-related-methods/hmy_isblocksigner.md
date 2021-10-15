# hmy_isBlockSigner

## Description

hmy_isBlockSigner returns true is validator signed a particular block or not

## API v1

### Parameters

1. `String` - block number in string 0x format
2. `String` - validator one address ("one1...")

### Returns

* `Bool` - true if validator signed block, false otherwise 

### Sample Curl Request

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_isBlockSigner",
    "params": ["0x1", "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"],
    "id": 1
}' -H "Content-Type: application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": true
}
```

## API v2

### Parameters

1. `Number` - block number
2. `String` - validator one address ("one1...")

### Returns

* `Bool` - true if validator signed block, false otherwise 

### Sample Curl Request

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmyv2_isBlockSigner",
    "params": [1, "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"],
    "id": 1
}' -H "Content-Type: application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": true
}
```
