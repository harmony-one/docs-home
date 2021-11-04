---
description: How to see your current validator information
---

# Checking Validator Information

You can check your validator’s information using the CLI with the following command:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy blockchain validator information [ONE ADDRESS] --node="https://api.s0.t.hmny.io"
```
{% endtab %}

{% tab title="Testnet" %}
```bash
./hmy blockchain validator information [ONE ADDRESS] --node="https://api.s0.b.hmny.io"
```
{% endtab %}
{% endtabs %}

## Example:

```bash
./hmy blockchain validator information one1925zlp5celp8r8jj3utpcxpjtncuuv2nu2449v --node="https://api.s0.t.hmny.io"
```

## Output:

```bash
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "current-epoch-performance": {
      "current-epoch-signing-percent": {
        "current-epoch-blocks-left": 9,
        "current-epoch-signed": 29,
        "current-epoch-signing-percentage": "1.000000000000000000",
        "current-epoch-to-sign": 29
      }
    },
    "currently-in-committee": true,
    "epos-status": "currently elected and signing enough blocks to be eligible for election next epoch",
    "lifetime": {
      "apr": "0.000000000000000000",
      "blocks": {
        "signed": 5879,
        "to-sign": 5880
      },
      "reward-accumulated": 6.966841018353012e+21
    },
    "metrics": {
      "by-shard": [
        {
          "bls-public-key": "3a26c230170cb295a20931661967ebc3bd817859e11d1eecda5cabb9ad372cd6cbba7843a72a24f24352dc3757aad014",
          "earning-account": "one1925zlp5celp8r8jj3utpcxpjtncuuv2nu2449v",
          "effective-stake": "250000000000000000000000.000000000000000000",
          "group-percent": "0.035843835577157440",
          "overall-percent": "0.011470027384690381",
          "shard-id": 0
        }
      ],
      "total-effective-stake": "250000000000000000000000.000000000000000000"
    },
    "total-delegation": 2.5e+23,
    "validator": {
      "address": "one1925zlp5celp8r8jj3utpcxpjtncuuv2nu2449v",
      "bls-public-keys": [
        "3a26c230170cb295a20931661967ebc3bd817859e11d1eecda5cabb9ad372cd6cbba7843a72a24f24352dc3757aad014"
      ],
      "creation-height": 12037,
      "delegations": [
        {
          "amount": 1.5e+23,
          "delegator-address": "one1925zlp5celp8r8jj3utpcxpjtncuuv2nu2449v",
          "reward": 6.149775864909033e+21,
          "undelegations": []
        },
        {
          "amount": 1e+23,
          "delegator-address": "one1jjq5pl4le0fhhu3n2znkkt9tydrzjcyzaljtnl",
          "reward": 620363080921910600000,
          "undelegations": []
        }
      ],
      "details": "S0",
      "identity": "J",
      "last-epoch-in-committee": 471,
      "max-change-rate": "0.100000000000000000",
      "max-rate": "0.500000000000000000",
      "max-total-delegation": 1e+25,
      "min-self-delegation": 1e+22,
      "name": "[R]",
      "rate": "0.100000000000000000",
      "security-contact": "J",
      "update-height": 12037,
      "website": "harmony.one"
    }
  }
}
```

{% hint style="warning" %}
If your validator does not sign more than 2/3 of the blocks in an epoch, the validator will be removed from the pool of eligible validators.

In order to be included in the pool again, you will have to use send an [Edit Validator transaction](changing-validator-information.md) with `--active true.`
{% endhint %}
