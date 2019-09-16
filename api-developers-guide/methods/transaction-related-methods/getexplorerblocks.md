---
description: GetExplorerTx returns information about the requested transaction.
---

# tx

**HTTP Request Endpoints**

| Chains | URLs |
| :--- | :--- |
| mainnet | TBD |
| betaNet | e0.b.hmny.io:5000 |
| local | localhost:5099 |

{% api-method method="get" host="107.21.71.80:5000" path="/tx?id=0x44479ab2140f6bbd198355a45d04a70314f8861c5969d9a1b05121fec3e6b07c" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
hex transaction ID
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
    "id": "0x44479ab2140f6bbd198355a45d04a70314f8861c5969d9a1b05121fec3e6b07c",
    "timestamp": "",
    "from": "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy",
    "to": "one1uyshu2jgv8w465yc8kkny36thlt2wvel89tcmg",
    "value": "220",
    "bytes": "",
    "data": ""
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

