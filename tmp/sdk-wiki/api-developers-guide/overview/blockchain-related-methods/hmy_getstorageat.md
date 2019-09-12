---
description: GetStorageAt
---

# hmy\_getStorageAt

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
| method | "hmy\_getStorageAt" |
| params | \["0xD7Ff41CA29306122185A07d04293DdB35F24Cf2d", "0", "latest"\] |
| "1" |  |

**Sample Curl Request**

```text
curl -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getStorageAt",
    "params":[
    "0xD7Ff41CA29306122185A07d04293DdB35F24Cf2d", "0", "latest"],
    "id":1
}'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x0000000000000000000000000000000000000000000000000000000000000000"
}
```

