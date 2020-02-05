# hmy\_getValidators

## Description

hmy\_getValidators returns list of validators for a particular epoch in corresponding shard

## Parameters

1. `Uint64` - epoch number

## Returns

* `shardID` - `Uint32` - shard id
* `validators` - `Array` : list of validators in below format
  * `address` - `String` : one address
  * `balance` - `String` : validator current balance \(will be replaced with stake soon\) 0x format

## Sample Curl Request

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getValidators",
    "params":[0],
    "id":1

}' -H "Content-Type: application/json" -X POST "http://localhost:9500"
```

## **Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "shardID": 0,
        "validators": [
            {
                "address": "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy",
                "balance": "0x3763284988b12fdb3"
            },
            {
                "address": "one12fuf7x9rgtdgqg7vgq0962c556m3p7afsxgvll",
                "balance": "0x376322519535f6db3"
            },
            {
                "address": "one1pf75h0t4am90z8uv3y0dgunfqp4lj8wr3t5rsp",
                "balance": "0x376322519535f6dbc"
            },
            {
                "address": "one1spshr72utf6rwxseaz339j09ed8p6f8ke370zj",
                "balance": "0x36f416a4047f9ddb3"
            },
            {
                "address": "one1d2rngmem4x2c6zxsjjz29dlah0jzkr0k2n88wc",
                "balance": "0x45a3027c55a812498"
            },
            {
                "address": "one1a50tun737ulcvwy0yvve0pvu5skq0kjargvhwe",
                "balance": "0x30f1a8ebe2ec1b6d8"
            },
            {
                "address": "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7",
                "balance": "0x376322519535f6dbb"
            }
        ]
    }
}
```

