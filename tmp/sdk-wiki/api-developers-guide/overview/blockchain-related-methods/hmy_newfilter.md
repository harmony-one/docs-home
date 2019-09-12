---
description: NewFilter
---

# hmy\_newFilter

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
| method | "hmy\_newFilter" |
| params | \[{"BlockHash": "0x5725b5b2ab28206e7256a78cda4f9050c2629fd85110ffa54eacd2a13ba68072"}\] |
| id | "1" |

**Sample Curl Request**

```text
curl   -d '{
    "jsonrpc":"2.0", 
    "method":"hmy_newFilter", 
    "params":[
    {"BlockHash": "0x5725b5b2ab28206e7256a78cda4f9050c2629fd85110ffa54eacd2a13ba68072"}],
    "id":1
}'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x58010795a282878ed0d61da72a14b8b0"
}
```

