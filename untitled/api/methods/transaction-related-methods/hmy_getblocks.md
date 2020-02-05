# hmy\_getBlocks

## Description

hmy\_getBlocks returns blocks in range \[from; to\]

## Parameters

1. `String` - starting block number in 0x format
2. `String` - ending block number in 0x format
3. `blockArgs` - optional args struct in json format \(should be used just with { }\)
   1. `fullTx` - `Bool`: To show full tx or not
   2. `withSigners`- `Bool`: Include block signes in blocks or not

## Returns

* `Array` : returns blocks list in json format
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
  * `transactions` - `Array`: Array of transaction objects; absent if second parameter is `false`.
  * `signers` - `Array`: Array of validators one addresses who signed this block
  * `uncles` - `Array`: Array of uncle hashes.

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getBlocks",
    "params":[
        "0x0",
        "0x1", 
        {
            "withSigners": true, 
            "fullTx": true
        }
    ],
    "id":1
}' -H "Content-Type: application/json" -X POST "http://localhost:9500"
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
        {
            "difficulty": 0,
            "extraData": "0x4861726d6f6e7920666f72204f6e6520616e6420416c6c2e204f70656e20436f6e73656e73757320666f72203130422e",
            "gasLimit": "0x47e7c4",
            "gasUsed": "0x0",
            "hash": "0x34a8b155f90b8fc22342fc8b5d1c969ed836a2f666c506e4017b570dc337e88c",
            "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
            "miner": "0x0000000000000000000000000000000000000000",
            "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
            "nonce": 0,
            "number": "0x0",
            "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
            "receiptsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
            "signers": [],
            "size": "0x6ed",
            "stateRoot": "0xae22370df046aa8c4470a032ecc88609efc08438abe79fd9e7f134b077a11fb6",
            "timestamp": "0x5d162b70",
            "transactions": [],
            "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
            "uncles": []
        },
        {
            "difficulty": 0,
            "extraData": "0x",
            "gasLimit": "0x47f9bc",
            "gasUsed": "0x0",
            "hash": "0x9e91a1ebe860eab3821f0d731689ec3833863f445a6f79649ce2813782e36be2",
            "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
            "miner": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016",
            "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
            "nonce": 0,
            "number": "0x1",
            "parentHash": "0x34a8b155f90b8fc22342fc8b5d1c969ed836a2f666c506e4017b570dc337e88c",
            "receiptsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
            "signers": [
                "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy",
                "one12fuf7x9rgtdgqg7vgq0962c556m3p7afsxgvll",
                "one1pf75h0t4am90z8uv3y0dgunfqp4lj8wr3t5rsp",
                "one1spshr72utf6rwxseaz339j09ed8p6f8ke370zj",
                "one1d2rngmem4x2c6zxsjjz29dlah0jzkr0k2n88wc",
                "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"
            ],
            "size": "0x33b",
            "stateRoot": "0xae22370df046aa8c4470a032ecc88609efc08438abe79fd9e7f134b077a11fb6",
            "timestamp": "0x5db74a3f",
            "transactions": [],
            "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
            "uncles": []
        }
    ]
}
```

