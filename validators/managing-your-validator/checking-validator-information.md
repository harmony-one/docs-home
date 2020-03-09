# Checking Validator Information



You can check your validator information using the following command

{% tabs %}
{% tab title="Open Staking Testnet" %}
```text
./hmy --node=https://api.s0.os.hmny.io/ blockchain validator information [ONE ADDRESS]
```
{% endtab %}

{% tab title="Partner Testnet" %}
```
./hmy --node=https://api.s0.ps.hmny.io/ blockchain validator information [ONE ADDRESS]
```
{% endtab %}
{% endtabs %}

Example output below:

```text
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "active": true,
    "address": "one1337twjy8nfcwxzjqrc6lgqxxhs0zeult242ttw",
    "availability": {
      "num-blocks-signed": 15448,
      "num-blocks-to-sign": 15450
    },
    "banned": false,
    "bls-public-keys": [
      "426739d753d36fbe34f8782c01faf0c224e6fbb764fb08339010195b8e657893b8ae4f9bcdad451060518e07a87b418e"
    ],
    "creation-height": 173,
    "delegations": [
      {
        "amount": 1.11111e+23,
        "delegator-address": "one1337twjy8nfcwxzjqrc6lgqxxhs0zeult242ttw",
        "reward": 5.037996235473647e+22,
        "undelegations": []
      },
      {
        "amount": 79000000000000000000,
        "delegator-address": "one15uwuu2kwth75xxspzn7r4ja2cnhtpgqkvnpgh0",
        "reward": 20531163112060826000,
        "undelegations": []
      },
      {
        "amount": 0,
        "delegator-address": "one1zksj3evekayy90xt4psrz8h6j2v3hla4qwz4ur",
        "reward": 0,
        "undelegations": []
      }
    ],
    "details": "Yo waddup",
    "identity": "Harmony Test",
    "last-epoch-in-committee": 204,
    "max-change-rate": "0.155456293704318700",
    "max-rate": "0.750000000000000000",
    "max-total-delegation": 1e+24,
    "min-self-delegation": 1e+23,
    "name": "BBQ Validator",
    "rate": "0.123000000000000000",
    "security-contact": "Daniel-VDM",
    "update-height": 173,
    "website": "harmony.one"
  }
}
```

{% hint style="warning" %}
If your validator does not sign 66% of the blocks in an epoch, the validator will be removed from the pool of eligible validators.

In order to be included in the pool again, you will have to use send an [Edit Validator transaction](https://docs.harmony.one/validators/validator/managing-your-validator/changing-your-validator-profile) with `--active true`.
{% endhint %}

