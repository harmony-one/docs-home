---
description: GetExplorerShard returns explorer nodes hashes in the network.
---

# shard

Returns explorer node hashes of a given shard.

#### Parameters

{% hint style="info" %}
Make sure to change the explorer endpoint to match the shard ID.
{% endhint %}

* `id` - `Integer` - Shard ID to query.

#### Returns

* `nodes` - `Array`
  * `id` - `String` - Explorer node hash.

#### Sample Curl Request

```bash
curl -H "Content-Type:application/json" -X GET "e1.b.hmny.io:5000/shard?id=1"
```

#### Sample Curl Response

```javascript
{
  "nodes": [
    {
      "id": "QmXh6ZW5XG9uKLnycMnPtuQoAMJ8rSKfJt1LLxTfSGAqKv"
    },
    {
      "id": ""
    }
  ]
}
```

