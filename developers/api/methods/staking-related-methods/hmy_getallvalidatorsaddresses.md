---
description: hmy_getAllValidatorAddresses
---

# hmy\_getAllValidatorAddresses

Returns complete validators addresses list

## Returns

* `Array`
  * `String` - validator address

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getAllValidatorAddresses",
    "params":[],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'https://api.s0.b.hmny.io'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": ["one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"]
}
```
