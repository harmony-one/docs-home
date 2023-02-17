# hmy\_getBlockSigners

## Description

hmy\_getBlocksSigners returns list of block signers

## API v1

### Parameters

1. `String` - block number in string 0x format

### Returns

* `Array` of `String`: one addresses list of validators who signed this block

### Sample Curl Request

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_getBlockSigners",
    "params": ["0x1"],
    "id": 1
}' -H "Content-Type: application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
        "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy",
        "one12fuf7x9rgtdgqg7vgq0962c556m3p7afsxgvll",
        "one1pf75h0t4am90z8uv3y0dgunfqp4lj8wr3t5rsp",
        "one1spshr72utf6rwxseaz339j09ed8p6f8ke370zj",
        "one1d2rngmem4x2c6zxsjjz29dlah0jzkr0k2n88wc",
        "one1a50tun737ulcvwy0yvve0pvu5skq0kjargvhwe",
        "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"
    ]
}
```

## API v2

### Parameters

1. `Number` - block number

### Returns

* `Array` of `String`: one addresses list of validators who signed this block

### Sample Curl Request

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_getBlockSigners",
    "params": [1],
    "id": 1
}' -H "Content-Type: application/json" -X POST "https://api.s0.b.hmny.io"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
        "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy",
        "one12fuf7x9rgtdgqg7vgq0962c556m3p7afsxgvll",
        "one1pf75h0t4am90z8uv3y0dgunfqp4lj8wr3t5rsp",
        "one1spshr72utf6rwxseaz339j09ed8p6f8ke370zj",
        "one1d2rngmem4x2c6zxsjjz29dlah0jzkr0k2n88wc",
        "one1a50tun737ulcvwy0yvve0pvu5skq0kjargvhwe",
        "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"
    ]
}
```
