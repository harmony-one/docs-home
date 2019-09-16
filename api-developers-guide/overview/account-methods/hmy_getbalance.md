---
description: GetBalance
---

# hmy\_getBalance

Get the balance of an address at a given block.

#### Parameters

1. `String` -  The address to get the balance of.
2. `String` - Block to get query for balance; "latest" gives latest block.

#### Returns

* `String` - The current balance for the given address in ATTO.

#### Sample Curl Request

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

