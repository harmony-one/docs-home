# hmy\_newBlockFilter

**Parameters**

None

**Returns**

`QUANTITY` - A filter id.

**Example**

```text
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_newBlockFilter","params":[],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":  "2.0",
  "result": "0x1" // 1
}
```

