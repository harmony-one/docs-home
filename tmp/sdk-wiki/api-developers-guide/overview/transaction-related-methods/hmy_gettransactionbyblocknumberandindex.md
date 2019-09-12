---
description: GetTransactionByBlockNumberAndIndex
---

# hmy\_getTransactionByBlockNumberAndIndex

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
| method | "hmy\_getTransactionByBlockNumberAndIndex" |
| params | \["0x4", "0x0"\] |
| id | "1" |

**Sample Curl Request**

```text
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getTransactionByBlockNumberAndIndex",
    "params":[
    "0x4", "0x0"],
    "id":1
}'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockHash": "0x428ead93e632d5255ea3d1fb61b02ab8493cf562a398af2159c33ecd53c62c16",
        "blockNumber": "0x4",
        "from": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016",
        "gas": "0x5208",
        "gasPrice": "0x0",
        "hash": "0xa7bb2c7cbfe4f5d6cf061aacd9d0dce7660d1f82da63dd7c76d9e856c1dc0278",
        "input": "0x",
        "nonce": "0x0",
        "to": "0x3aea49553ce2e478f1c0c5acc304a84f5f4d1f98",
        "transactionIndex": "0x0",
        "value": "0xde0b6b3a7640000",
        "v": "0x1b",
        "r": "0x3cb6eedb11cad81f1ab52d72f46dcea0b3d7f46beaf40e83660b165546db5fc6",
        "s": "0x1bc4b99089ab7d3ec17eae9d8a366feac87f9a76dd3ae031abfb86359b020551"
    }
}
```

