---
description: hmy_getActiveValidatorsAddresses
---

# hmy\_getElectedValidatorAddresses

Returns elected validators addresses list

## Returns

* `Array`
  * `String` - validator address

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getElectedValidatorAddresses",
    "params":[],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'https://api.harmony.one'
```

**Sample Curl Response**

```bash
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": ["one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"]
}
```
