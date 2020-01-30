# hmy\_getEpoch

## Description

hmy\_getEpoch returns current epoch of shard

## Parameters

## Returns

* `String` - Current requested node shard epoch 0x format

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_getEpoch",
    "params": [],
    "id": 1
}' -H "Content-Type: application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0xc"
}
```

{% hint style="info" %}
If Node.js is installed on your system, one easy way to convert hexadecimal balances into a more readable decimal format is to run `node -e "console.log(<balance>)"`
{% endhint %}

