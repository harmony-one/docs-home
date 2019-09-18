---
description: GetBlockTransactionCountByHash
---

# hmy\_getBlockTransactionCountByHash

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
| method | "hmy\_getBlockTransactionCountByHash" |
| params | \["0x660fe701f580ffebfcfb4af1836c9929c1fd0014d8d79d60749fecf52df7a90d"\] |
| id | "1" |

**Sample Curl Request**

```text
curl   -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getBlockTransactionCountByHash",
    "params":[
    "0x660fe701f580ffebfcfb4af1836c9929c1fd0014d8d79d60749fecf52df7a90d"],
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

