---
description: Call
---

# hmy\_call

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
| method | "hmy\_call" |
| params | \[{"to": "0x08AE1abFE01aEA60a47663bCe0794eCCD5763c19", "latest"\] |
| id | "1" |

**Sample Curl Request**

```text
curl -d '{
"jsonrpc":"2.0",
"method":"hmy_call",
"params":[
	{"to": "0x08AE1abFE01aEA60a47663bCe0794eCCD5763c19"},
	"latest"],
	"id":1
}'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x"
}
```



