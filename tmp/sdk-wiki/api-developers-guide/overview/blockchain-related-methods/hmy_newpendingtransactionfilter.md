---
description: NewPendingTransactionFilter
---

# hmy\_newPendingTransactionFilter

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
| method | "hmy\_newPendingTransactionFilter" |
| params | \[\] |
| id | "1" |

**Sample Curl Request**

```text
curl   -d '{
    "jsonrpc":"2.0", 
    "method":"hmy_newPendingTransactionFilter", 
    "params":[
    ],
    "id":1
}'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x547e06b35ba8dcc8674977e11a35cffe"
}
```

