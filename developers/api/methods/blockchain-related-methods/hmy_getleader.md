# hmy_getLeader

## Description

hmy_getLeader returns one address of current shard leader node

## Returns

* `String` - returns one address of current shard leader node

**Sample Curl Request**

```bash
 curl -d '{
    "jsonrpc": "2.0",
    "method": "hmy_getLeader",
    "params": [],
    "id": 1
}' -H 'Content-Type:application/json' -X POST 'http://api.s0.b.hmny.io'
```

**Sample Curl Response**

```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy"
}
```
