# hmy\_getValidators

## Parameters

1. `uint64` - epoch number

## Returns

* `[]Validators` - full format shown in response

## Sample Curl Request

```bash
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "hmy_getBalance",
    "params": [
        "one1z05g55zamqzfw9qs432n33gycdmyvs38xjemyl", 
        "latest"
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

