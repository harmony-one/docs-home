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
    "current-epoch-signing-percent": {
      "current-epoch-signed": 65,
      "current-epoch-to-sign": 72,
      "percentage": "0.902777777777777778"
    },
    "current-epoch-voting-power": [
      {
        "effective-stake": "15300000000000000000000.000000000000000000",
        "shard-id": 2,
        "voting-power-adjusted": "0.021808463251670379",
        "voting-power-raw": "0.068151447661469933"
      }
    ],
    "validator": {
      "active": true,
      "address": "one1337twjy8nfcwxzjqrc6lgqxxhs0zeult242ttw",
      "availability": {
        "num-blocks-signed": 3352,
        "num-blocks-to-sign": 3413
      },
      "banned": false,
      "bls-public-keys": [
        "426739d753d36fbe34f8782c01faf0c224e6fbb764fb08339010195b8e657893b8ae4f9bcdad451060518e07a87b418e"
      ],
      "creation-height": 1499,
      "delegations": [
        {
          "amount": 1.1111e+22,
          "delegator-address": "one1337twjy8nfcwxzjqrc6lgqxxhs0zeult242ttw",
          "reward": 2.6205838731636302e+22,
          "undelegations": []
        }
      ],
      "details": "Yo waddup",
      "identity": "Harmony Test",
      "last-epoch-in-committee": 66,
      "max-change-rate": "0.155456293704318700",
      "max-rate": "0.750000000000000000",
      "max-total-delegation": 1e+24,
      "min-self-delegation": 1e+22,
      "name": "BBQ Validator",
      "rate": "0.100000000000000000",
      "security-contact": "Daniel-VDM",
      "update-height": 1499,
      "website": "harmony.one"
    }
  }
}
```

{% hint style="warning" %}
If your validator does not sign 66% of the blocks in an epoch, the validator will be removed from the pool of eligible validators.

In order to be included in the pool again, you will have to use send an [Edit Validator transaction](https://docs.harmony.one/validators/validator/managing-your-validator/changing-your-validator-profile) with `--active true`.
{% endhint %}

