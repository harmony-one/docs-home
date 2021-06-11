---
description: How to collect your rewards
---

# Collecting Rewards

You can collect your rewards with the following command:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" staking collect-rewards \
--delegator-addr [ONE ADDRESS] --passphrase
```
{% endtab %}

{% tab title="Testnet" %}
```bash
./hmy --node="https://api.s0.b.hmny.io" staking collect-rewards \
--delegator-addr [ONE ADDRESS] --passphrase
```
{% endtab %}
{% endtabs %}

## Example:

```bash
./hmy --node="https://api.s0.t.hmny.io" staking collect-rewards \
--delegator-addr one1km7xg8e3xjys7azp9f4xp8hkw79vm2h3f2lade --passphrase
```

The CLI will prompt your for the passphrase of the delegation account.

`--delegator-addr` is the account to collect rewards for

{% hint style="warning" %}
You can only collect ALL of your block rewards at once, not partially.
{% endhint %}

