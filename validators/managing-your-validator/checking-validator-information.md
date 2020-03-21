# Checking Validator Information

You can check your validator information using the following command:

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

Output example below:

```text
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "current-epoch-signing-percent": {
      "current-epoch-signed": 0,
      "current-epoch-to-sign": 2,
      "percentage": "0.000000000000000000"
    },
    "current-epoch-voting-power": [
      {
        "effective-stake": "9665865000000000000000.000000000000000000",
        "shard-id": 0,
        "voting-power-adjusted": "0.044606060606060606",
        "voting-power-raw": "0.139393939393939394"
      }
    ],
    "validator": {
      "address": "one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd",
      "availability": {
        "num-blocks-signed": 0,
        "num-blocks-to-sign": 75
      },
      "bls-public-keys": [
        "bf3c6ec088cd66fdb540860bd6505b272230164b0510d5f470042d47118d4c8bbe005d28e5de5e489fa22e4ca450c080"
      ],
      "creation-height": 3675,
      "delegations": [
        {
          "amount": 2.5e+22,
          "delegator-address": "one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd",
          "reward": 0,
          "undelegations": []
        }
      ],
      "details": "Soph P-OPS Validator node",
      "epos-eligibility-status": "active",
      "identity": "Soph",
      "last-epoch-in-committee": 50,
      "max-change-rate": "0.050000000000000000",
      "max-rate": "0.900000000000000000",
      "max-total-delegation": 1e+24,
      "min-self-delegation": 2000000000000000000,
      "name": "Soph P-OPS Validator node",
      "rate": "0.100000000000000000",
      "security-contact": "Soph",
      "update-height": 3675,
      "website": "soph.harmony.one"
    }
  }
}
```

{% hint style="warning" %}
If your validator does not sign 66% of the blocks in an epoch, the validator will be removed from the pool of eligible validators.

In order to be included in the pool again, you will have to use send an [Edit Validator transaction](https://docs.harmony.one/validators/validator/managing-your-validator/changing-your-validator-profile) with `--active true.`
{% endhint %}

