---
description: GetExplorerShard returns explorer nodes hashes in the network.
---

# shard

Returns explorer node hashes of a given shard.

#### Parameters

{% hint style="danger" %}
Currently, `id` does not change which shard is queried; only the explorer endpoint \(`e0` or `e1`\) determines which shard is queried. Thus, `id` is optional.
{% endhint %}

* `id` - `Integer` - _\(Optional\)_ Shard ID to query.

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

