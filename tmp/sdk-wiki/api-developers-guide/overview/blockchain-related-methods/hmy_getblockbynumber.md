---
description: GetBlockByNumber
---

# hmy\_getBlockByNumber

**HTTP Request Endpoints**

| Chains | URLs |
| :--- | :--- |
| mainnet | TBD |
| betaNet | http://l0.b.hmny.io:9500 |
| local | http://localhost:9500 |

**Arguments**

| Request Data Object | Example |
| :--- | :--- |
| jsonrpc | "2.0" |
| method | "hmy\_getBlockByNumber" |
| params | \["0x66", true\] |
| id | "1" |

**Sample Curl Request**

```text
curl   -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getBlockByNumber",
    "params":[
    "0x66", true],
    "id":1
}'
```

**Sample Curl Response**

```text
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

