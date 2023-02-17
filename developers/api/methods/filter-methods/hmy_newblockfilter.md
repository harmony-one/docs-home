# hmy\_newBlockFilter

**Parameters**

None

**Returns**

`QUANTITY` - A filter id.

**Example**

```
// Request
curl -d '{"jsonrpc":"2.0","method":"eth_newBlockFilter","params":[],"id":73}' -H "Content-Type:application/json" -X POST "https://api.s0.b.hmny.io"

// Result
{
  "id":1,
  "jsonrpc":  "2.0",
  "result": "0x1" // 1
} 
```
