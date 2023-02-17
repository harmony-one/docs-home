---
description: hmy_getFilterLogs
---

# hmy\_getFilterLogs

Returns an array of all logs matching filter with given id.

**Parameters**

1. `QUANTITY` - The filter id.

**Example Parameters**

```
params: [
  "0x16" // 22
]
```

**Returns**

See hmy\_getFilterChanges

**Example**

```
// Request
curl -d '{"jsonrpc":"2.0","method":"hmy_getFilterLogs","params":["0x16"],"id":74}' -H "Content-Type:application/json" -X POST "https://api.s0.b.hmny.io"
```

Result see hmy\_getFilterChanges
