---
description: GetBlockTransactionCountByNumber
---

# hmy\_getBlockTransactionCountByNumber

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
| method | "hmy\_getBlockTransactionCountByNumber" |
| params | \["0x66"\] |
| id | "1" |

**Sample Curl Request**

```text
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getBlockTransactionCountByNumber",
    "params":["0x66"],
    "id":1
}'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x0"
}
```

