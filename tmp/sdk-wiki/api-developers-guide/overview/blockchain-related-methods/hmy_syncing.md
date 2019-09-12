---
description: Syncing
---

# hmy\_syncing

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
| method | "hmy\_syncing" |
| params | \[\] |
| id | "1" |

**Sample Curl Request**

```text
-d '{
    "jsonrpc":"2.0",
    "method":"hmy_syncing",
    "params":[],
    "id":1
}'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": false
}
```

