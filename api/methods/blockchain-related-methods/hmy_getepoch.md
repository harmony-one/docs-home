# hmy\_getEpoch

## Parameters

## Returns

* `uint64` - Current requested node shard epoch

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

{% hint style="info" %}
If Node.js is installed on your system, one easy way to convert hexadecimal balances into a more readable decimal format is to run `node -e "console.log(<balance>)"`
{% endhint %}

