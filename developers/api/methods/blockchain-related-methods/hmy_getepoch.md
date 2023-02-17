# hmy\_getEpoch

## Description

hmy\_getEpoch returns current epoch of shard

## Parameters

## API v1

**Returns**

* `String` - Current requested node shard epoch 0x format

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_getEpoch",
    "params": [],
    "id": 1
}' -H "Content-Type: application/json" -X POST "https://api.s0.b.hmny.io"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0xc"
}
```

## API v2

**Returns**

* `uint64` - Current requested node shard epoch decimal format

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmyv2_getEpoch",
    "params": [],
    "id": 1
}' -H "Content-Type: application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": 10
}
```

{% hint style="info" %}
If Node.js is installed on your system, one easy way to convert hexadecimal balances into a more readable decimal format is to run `node -e "console.log(<balance>)"`
{% endhint %}
