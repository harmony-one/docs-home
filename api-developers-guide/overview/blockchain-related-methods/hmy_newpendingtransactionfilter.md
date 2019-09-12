---
description: NewPendingTransactionFilter
---

# hmy\_newPendingTransactionFilter

**HTTP Request Endpoints**

| Chains | URLs |
| :--- | :--- |
| mainnet | TBD |
| betaNet | [http://l0.b.hmny.io:9500](http://l0.b.hmny.io:9500) |
| local | [http://localhost:9500](http://localhost:9500) |

**Arguments**

| Request Data Object | Example |
| :--- | :--- |
| jsonrpc | "2.0" |
| method | "hmy\_newPendingTransactionFilter" |
| params | \[\] |
| id | "1" |

**Sample Curl Request**

```bash
curl -d '{
    "jsonrpc":"2.0", 
    "method":"hmy_newPendingTransactionFilter", 
    "params":[
    ],
    "id":1
}' -H 'Content-Type:application/json' -X POST 'http://l0.b.hmny.io:9500'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x547e06b35ba8dcc8674977e11a35cffe"
}
```

