---
description: trace_block
---

# trace\_transaction

Get the transaction trace information

## Returns

* `JSON containing the trace information`

**Sample Curl Request**

```bash
curl --location --request POST 'https://a.api.s0.t.hmny.io' \
--header 'Content-Type: application/json' \
--data-raw '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "trace_transaction",
    "params": ["0x0d449c8dde6c13e63064f49c531ba028878a4de368473cdff421255000c8047f"]
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
      "transactionHash": "0x0d449c8dde6c13e63064f49c531ba028878a4de368473cdff421255000c8047f",
      "transactionPosition": 79,
      "subtraces": 0,
      "traceAddress": [],
      "type": "call",
      "action": {
        "callType": "call",
        "value": "0x0",
        "to": "0x9b68bf4bf89c115c721105eaf6bd5164afcc51e4",
        "gas": "0x37c04",
        "from": "0x43c0f652a54c5d986040683a0b30dfaaee6135ba",
        "input": "0xa9059cbb000000000000000000000000f389b9b05367352e898b401c239a98f85b2ec8b00000000000000000000000000000000000000000000000004d195062a85e8000"
      },
      "result": {
        "output": "0x0000000000000000000000000000000000000000000000000000000000000001",
        "gasUsed": "0x3cdf"
      }
    }
  ]
}
```
