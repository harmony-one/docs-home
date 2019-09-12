---
description: >-
  GetExplorerCommittee returns a list of network of a particular shard
  (shard_id) and epoch. To get current list of validators you should pass epoch
  from current block.
---

# committee

**HTTP Request Endpoints**

| Chains | URLs |
| :--- | :--- |
| mainnet | TBD |
| betaNet | e0.b.hmny.io:5000 |
| local | localhost:5099 |

{% api-method method="get" host="107.21.71.80:5000" path="/committee?shard\_id=0&epoch=0" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="shard\_id" type="integer" required=false %}
defaults to 0
{% endapi-method-parameter %}

{% api-method-parameter name="epoch" type="integer" required=false %}
defaults to current block epoch
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
    "validators": [
        {
            "address": "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy",
            "balance": 58057142857142857139
        },
        {
            "address": "one12fuf7x9rgtdgqg7vgq0962c556m3p7afsxgvll",
            "balance": 58057142857142857139
        },
        {
            "address": "one1pf75h0t4am90z8uv3y0dgunfqp4lj8wr3t5rsp",
            "balance": 58057142857142857148
        },
        {
            "address": "one1spshr72utf6rwxseaz339j09ed8p6f8ke370zj",
            "balance": 58057142857142857139
        },
        {
            "address": "one1d2rngmem4x2c6zxsjjz29dlah0jzkr0k2n88wc",
            "balance": 58057142857142857148
        },
        {
            "address": "one1a50tun737ulcvwy0yvve0pvu5skq0kjargvhwe",
            "balance": 38057142857142857139
        },
        {
            "address": "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7",
            "balance": 58057142857142857148
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

