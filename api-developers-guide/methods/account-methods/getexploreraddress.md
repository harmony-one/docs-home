---
description: GetExplorerAddress returns the address of the requested explorer node.
---

# address

**HTTP Request Endpoints**

| Chains | URLs |
| :--- | :--- |
| mainnet | TBD |
| betaNet | e0.b.hmny.io:5000 |
| local | localhost:5099 |
|  |  |

#### Parameters

1. `String` -  The address to get the balance of.
2. `String` - Block to get query for balance; "latest" gives latest block.

#### Result

{% api-method method="get" host="107.21.71.80:5000" path="/address?id=" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
hex address
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
    "id": "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy",
    "balance": 172723809523809523801,
    "txs": null
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



