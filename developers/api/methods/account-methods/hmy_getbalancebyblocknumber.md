---
description: hmy_getBalanceByBlockNumber
---

# hmy\_getBalanceByBlockNumber

Get the balance of an address at a given block.

## API v1

#### Parameters

1. `String` -  The address to get the balance of
2. `String` - Block to get query for balance

#### Returns

* `String` - The current balance for the given address in ATTO.

#### Sample Curl Request

```bash
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "hmy_getBalanceByBlockNumber",
    "params": [
        "one1z05g55zamqzfw9qs432n33gycdmyvs38xjemyl", 
        "0x1"
    ]
}' -H "Content-Type: application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x6046f35fca29af800"
}
```

## API v2

#### Parameters

1. `String` -  The address to get the balance of
2. `Number` - Block to get query for balance

#### Returns

* `String` - The big.Int balance for the given address on a particular block.

#### Sample Curl Request

```bash
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "hmyv2_getBalanceByBlockNumber",
    "params": [
        "one1z05g55zamqzfw9qs432n33gycdmyvs38xjemyl",
        1
    ]
}' -H "Content-Type: application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "1000000000000"
}
```

