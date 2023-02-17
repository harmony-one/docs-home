# hmy\_getSignedBlocks

## Description

hmy\_getSigned blocks returns number of blocks out of last 1500 validator has signed

## Parameters

1. `String` - validator one address ("one1...")

## Returns

* `Number` - total number of signed blocks out of last 1500 blocks

## Sample Curl Request

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_getSignedBlocks",
    "params": ["one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"],
    "id": 1
}' -H "Content-Type: application/json" -X POST "https://api.s0.b.hmny.io"
```

## **Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x12"
}
```
