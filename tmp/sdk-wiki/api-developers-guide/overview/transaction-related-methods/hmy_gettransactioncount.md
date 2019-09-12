---
description: GetTransactionCount
---

# hmy\_getTransactionCount

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
| method | "hmy\_getTransactionCount" |
| params | \["0x806171f95C5a74371a19e8a312c9e5Cb4E1D24f6", "latest"\] |
| id | "1" |

**Sample Curl Request**

```text
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getTransactionCount",
    "params":[
    "0x806171f95C5a74371a19e8a312c9e5Cb4E1D24f6", "latest"],
    "id":1
}'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x3"
}
```

