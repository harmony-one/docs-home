---
description: GetTransactionReceipt
---

# hmy\_getTransactionReceipt

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
| method | "hmy\_getTransactionReceipt" |
| params | \["0x1dff358dad4d0fc95b11acc9826b190d8b7971ac26b3f7ebdee83c10cafaf86f"\] |
| id | "1" |

**Sample Curl Request**

```text
curl   -d '{
    "jsonrpc":"2.0",
    "method":"hmy_getTransactionReceipt",
    "params":[
    "0x1dff358dad4d0fc95b11acc9826b190d8b7971ac26b3f7ebdee83c10cafaf86f"],
    "id":1
}'
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockHash": "0xd6db4b8e899b25c584384a1369082c79f1a4a4d1c28a49d082507c4bce2a389e",
        "blockNumber": "0x14",
        "contractAddress": null,
        "cumulativeGasUsed": "0x5208",
        "from": "0x806171f95c5a74371a19e8a312c9e5cb4e1d24f6",
        "gasUsed": "0x5208",
        "logs": [],
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
        "root": "0xcd591734da7e2bbf6debad3e7c997020944947dc40dcf91cf54ddc7f5dba5828",
        "shardID": 0,
        "to": "0xd7ff41ca29306122185a07d04293ddb35f24cf2d",
        "transactionHash": "0x1dff358dad4d0fc95b11acc9826b190d8b7971ac26b3f7ebdee83c10cafaf86f",
        "transactionIndex": "0x0"
    }
}
```

