---
description: trace_block
---

# trace\_block

Get the block trace information

## Returns

* `Json containing block trace information`

**Sample Curl Request**

```bash
curl --location --request POST 'https://a.api.s0.t.hmny.io' \
--header 'Content-Type: application/json' \
--data-raw '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "trace_block",
    "params": ["0xE61019"]
}'
```

**Sample Curl Response**

```bash
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "blockNumber": 15077401,
      "blockHash": "0x16170404833ad82495d96a64a484fe26098e2ec70c11f9b681574771ce2ee073",
      "transactionHash": "0x581f40d605041c3e3577058d24f156bd8ed189e31f903bc3f3bf5083b3a4e14b",
      "transactionPosition": 0,
      "subtraces": 15,
      "traceAddress": [],
      "type": "call",
      "action": {
        "callType": "call",
        "value": "0x0",
        "to": "0x406989017988c7689159938aa7ff0ac51e1b773c",
        "gas": "0x5c7ac",
        "from": "0x01f2eb240a4e1187c9ee3f4125257f4716a32d75",
        "input": "0xae169a500000000000000000000000000000000000000000000000000000000000000004"
      },
      "result": {
        "output": "0x",
        "gasUsed": "0x4e41c"
      }
    },
    ...
}
```
