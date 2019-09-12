---
description: >-
  GetExplorerBlocks returns information about the requested block(s) specified
  by the inputted heights [from; to].
---

# blocks

**HTTP Request Endpoints**

| Chains | URLs |
| :--- | :--- |
| mainnet | TBD |
| betaNet | e0.b.hmny.io:5000 |
| local | localhost:5099 |

{% api-method method="get" host="107.21.71.80:5000" path="/blocks?from=0&to=0" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="from" type="integer" required=false %}
From which block to fetch blocks \(default is 0\)
{% endapi-method-parameter %}

{% api-method-parameter name="to" type="integer" required=false %}
Up to which block to fetch blocks \(default is last one\)
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
[
    {
        "height": "0",
        "id": "0xa427b2fa61d643bef9aefdb8fbc50aa25a8a72b6e0f7040576ee64aa32e01118",
        "txCount": "0",
        "timestamp": "1561734000000",
        "blockTime": 0,
        "merkleRoot": "0xae22370df046aa8c4470a032ecc88609efc08438abe79fd9e7f134b077a11fb6",
        "prevBlock": {
            "id": "",
            "height": ""
        },
        "bytes": "1678",
        "nextBlock": {
            "id": "0xb72cb0115abe3d68e2064f8c468a1f7ffe3b55ec04341131bbece23c78c578ca",
            "height": "1"
        },
        "txs": null,
        "signers": [
            "one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy",
            "one12fuf7x9rgtdgqg7vgq0962c556m3p7afsxgvll",
            "one1pf75h0t4am90z8uv3y0dgunfqp4lj8wr3t5rsp",
            "one1spshr72utf6rwxseaz339j09ed8p6f8ke370zj",
            "one1d2rngmem4x2c6zxsjjz29dlah0jzkr0k2n88wc",
            "one1a50tun737ulcvwy0yvve0pvu5skq0kjargvhwe",
            "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7"
        ],
        "epoch": 0,
        "extra_data": "Harmony for One and All. Open Consensus for 10B."
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

