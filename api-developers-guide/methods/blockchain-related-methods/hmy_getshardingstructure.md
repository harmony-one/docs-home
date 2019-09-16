---
description: GetShardingStructure
---

# hmy\_getShardingStructure

Returns the current shard of the node and lists API and WebSocket endpoints for each shard.

#### Returns

* `current` - `bool` - If the current node is on this shard.
* `http` - `String` - API endpoint for the shard.
* `shardID` - `Integer` - Shard ID.
* `ws` - `String` - WebSocket endpoint

#### Sample Curl Request

```bash
curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_getShardingStructure",
    "params": [],
    "id": 1
}' -H "Content-Type:application/json" -X POST "http://s0.b.hmny.io:9500"
```

#### Sample Curl Response

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
        {
            "current": true,
            "http": "https://api.s0.b.hmny.io",
            "shardID": 0,
            "ws": "wss://ws.s0.b.hmny.io"
        },
        {
            "current": false,
            "http": "https://api.s1.b.hmny.io",
            "shardID": 1,
            "ws": "wss://ws.s1.b.hmny.io"
        }
    ]
}
```

