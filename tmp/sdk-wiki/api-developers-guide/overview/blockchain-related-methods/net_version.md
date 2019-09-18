---
description: Net_Version
---

# net\_version

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
| method | "net\_version" |
| params | \[\] |
| id | "1" |

**Sample Curl Request**

```text
 curl -d '{
  "jsonrpc":"2.0",
  "method":"net_version",
  "params":[],
  "id":1
 }'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "1"
}
```

#### Sample Code

