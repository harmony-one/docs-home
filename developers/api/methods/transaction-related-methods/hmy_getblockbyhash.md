---
description: GetBlockByHash
---

# hmy_getBlockByHash

Get block by its hash.

## API v1

**Parameters**

1. `String` - The block hash. 
2. `Boolean` - If `true`, the returned block will contain all transactions in the block.

### Returns

* `number` - `Number`: The block number. `null` when its pending block.
* `hash` 32 Bytes - `String`: Hash of the block. `null` when its pending block.
* `parentHash` 32 Bytes - `String`: Hash of the parent block.
* `nonce` 8 Bytes - `String`: Hash of the generated proof-of-work. `null` when its pending block.
* `logsBloom` 256 Bytes - `String`: The bloom filter for the logs of the block. `null` when its pending block.
* `transactionsRoot` 32 Bytes - `String`: The root of the transaction trie of the block
* `stateRoot` 32 Bytes - `String`: The root of the final state trie of the block.
* `miner` - `String`: The address of the beneficiary to whom the mining rewards were given.
* `difficulty` - `String`: Integer of the difficulty for this block.
* `extraData` - `String`: The “extra data” field of this block.
* `size` - `Number`: Integer the size of this block in bytes.
* `gasLimit` - `Number`: The maximum gas allowed in this block.
* `gasUsed` - `Number`: The total used gas by all transactions in this block.
* `timestamp` - `Number`: The unix timestamp for when the block was collated.
* `stakingTransactions` - `Array`: Array of staking transactions object; are present by default
* `transactions` - `Array`: Array of transaction objects; absent if second parameter is `false`.
* `uncles` - `Array`: Array of uncle hashes.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getBlockByHash",
    "params":[
      "0x660fe701f580ffebfcfb4af1836c9929c1fd0014d8d79d60749fecf52df7a90d", 
      true]
    ],
    "id":1
}' -H "Content-Type:application/json" -X POST "http://l0.b.hmny.io:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "difficulty": 0,
        "extraData": "0x",
        "gasLimit": "0x4f6e2a",
        "gasUsed": "0x0",
        "hash": "0x660fe701f580ffebfcfb4af1836c9929c1fd0014d8d79d60749fecf52df7a90d",
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
        "miner": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016",
        "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "nonce": 0,
        "number": "0x66",
        "parentHash": "0xcac989d8ba18e88ab245686e491a171d46b759e85290a3fc6df80553d2ac582f",
        "receiptsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
        "size": "0x25d",
        "stateRoot": "0x830ff6830857f88bdc56141449d0729a663c6413dc0dc909fc1f3715dd576cee",
        "timestamp": "0x5d570a3f",
        "transactions": [],
        "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
        "uncles": []
    }
}
```

## API v2

**Parameters**

1. `String` - The block hash. 
2. `blockArgs` - optional args struct in json format (should be used just with { })
   1. `fullTx` - `Bool`: To show full tx or not
   2. `withSigners`- `Bool`: Include block signes in blocks or not
   3. `inclStaking` - `Bool`: To show staking txs or not

### Returns

* `number` - `Number`: The block number. `null` when its pending block.
* `hash` 32 Bytes - `String`: Hash of the block. `null` when its pending block.
* `parentHash` 32 Bytes - `String`: Hash of the parent block.
* `nonce` 8 Bytes - `String`: Hash of the generated proof-of-work. `null` when its pending block.
* `logsBloom` 256 Bytes - `String`: The bloom filter for the logs of the block. `null` when its pending block.
* `transactionsRoot` 32 Bytes - `String`: The root of the transaction trie of the block
* `stateRoot` 32 Bytes - `String`: The root of the final state trie of the block.
* `miner` - `String`: The address of the beneficiary to whom the mining rewards were given.
* `difficulty` - `String`: Integer of the difficulty for this block.
* `extraData` - `String`: The “extra data” field of this block.
* `size` - `Number`: Integer the size of this block in bytes.
* `gasLimit` - `Number`: The maximum gas allowed in this block.
* `gasUsed` - `Number`: The total used gas by all transactions in this block.
* `timestamp` - `Number`: The unix timestamp for when the block was collated.
* `stakingTransactions` - `Array`: Array of staking transactions object; absent if inclStaking is false, are present by default
* `transactions` - `Array`: Array of transaction objects; absent if second parameter is `false`.
* `uncles` - `Array`: Array of uncle hashes.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmyv2_getBlockByHash",
    "params":[
    "0x660fe701f580ffebfcfb4af1836c9929c1fd0014d8d79d60749fecf52df7a90d", 
    {
      "fullTx": true,
      "inclTx": true,
      "withSigners": true,
    }],
    "id":1
}' -H "Content-Type:application/json" -X POST "http://l0.b.hmny.io:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "difficulty": 0,
        "extraData": "0x",
        "gasLimit": 4716988,
        "gasUsed": 0,
        "hash": "0xa3b7dd8626bfc6f6037c06401ceaa752bb54f0539535aea9883170e305e3b6c5",
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
        "miner": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016",
        "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "nonce": 0,
        "number": 1,
        "parentHash": "0x34a8b155f90b8fc22342fc8b5d1c969ed836a2f666c506e4017b570dc337e88c",
        "receiptsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
        "signers": [
            "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy",
            "one12fuf7x9rgtdgqg7vgq0962c556m3p7afsxgvll",
            "one1pf75h0t4am90z8uv3y0dgunfqp4lj8wr3t5rsp",
            "one1spshr72utf6rwxseaz339j09ed8p6f8ke370zj",
            "one1d2rngmem4x2c6zxsjjz29dlah0jzkr0k2n88wc",
            "one1a50tun737ulcvwy0yvve0pvu5skq0kjargvhwe",
            "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"
        ],
        "size": 827,
        "stakingTransactions": [],
        "stateRoot": "0xae22370df046aa8c4470a032ecc88609efc08438abe79fd9e7f134b077a11fb6",
        "timestamp": 1580419937,
        "transactions": [],
        "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
        "uncles": []
    }
}
```
