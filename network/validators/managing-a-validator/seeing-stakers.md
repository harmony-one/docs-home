---
description: How to see your delegators
---

# Check Your Delegations

You can see the number of delegations to your validator with the following command:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy blockchain delegation by-validator [VALIDATOR ADDRESS] --node="https://api.s0.t.hmny.io"
```
{% endtab %}

{% tab title="Testnet" %}
```bash
./hmy blockchain delegation by-validator [VALIDATOR ADDRESS] --node="https://api.s0.b.hmny.io"
```
{% endtab %}
{% endtabs %}

### Example:

```bash
./hmy blockchain delegation by-validator one1km7xg8e3xjys7azp9f4xp8hkw79vm2h3f2lade --node="https://api.s0.t.hmny.io"
```

## Output:

```bash
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": [
    {
      "Undelegations": [],
      "amount": 93000000000000000000,
      "delegator_address": "one1ctr58xue32peagud620tmthc95w5ch94vfhfgp",
      "reward": 193348691324709180000,
      "validator_address": "one1ctr58xue32peagud620tmthc95w5ch94vfhfgp"
    },
    {
      "Undelegations": [],
      "amount": 1.01e+22,
      "delegator_address": "one1cg5d67v28m3s0xuph46y8w842yu9dzd7094zr5",
      "reward": 646413329184000700000,
      "validator_address": "one1ctr58xue32peagud620tmthc95w5ch94vfhfgp"
    }
  ]
}
```
