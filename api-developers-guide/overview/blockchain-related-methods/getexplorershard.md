---
description: GetExplorerShard returns explorer nodes hashes in the network.
---

# shard

**HTTP Request Endpoints**

| Chains | URLs |
| :--- | :--- |
| mainnet | TBD |
| betaNet | e0.b.hmny.io:5000 |
| local | localhost:5000 |

{% api-method method="get" host="107.21.71.80:5000" path="/shard?id=0" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="id" type="integer" required=false %}
Shard id \(default value is 0\)
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
    "nodes": [
        {
            "id": "QmbHoX6KqV1TsonrXkNj6LjphXcj2LtBucT7pExKYbVMLa"
        },
        {
            "id": ""
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

