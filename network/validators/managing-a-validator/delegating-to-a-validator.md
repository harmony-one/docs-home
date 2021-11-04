---
description: How to delegate tokens to a validator
---

# Delegating To A Validator

You can delegate tokens to a validator using the following command:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" staking delegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \
    --amount [AMOUNT] --passphrase
```
{% endtab %}

{% tab title="Testnet" %}
```bash
./hmy --node="https://api.s0.b.hmny.io" staking delegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \
    --amount [AMOUNT] --passphrase
```
{% endtab %}
{% endtabs %}

## Example:

```bash
./hmy --node="https://api.s0.t.hmny.io" staking delegate \
    --delegator-addr one1km7xg8e3xjys7azp9f4xp8hkw79vm2h3f2lade --validator-addr one1km7xg8e3xjys7azp9f4xp8hkw79vm2h3f2lade \
    --amount 10000 --passphrase
```

The CLI will ask for the passphrase for the `delegator-addr` keystore file.

`--delegator-addr` is the ONE address of the delegator** (string)**

`--validator-addr` is the ONE address of the validator** (string)**

`--amount` is the number of ONE tokens to delegate to the validator** (float)**

{% hint style="info" %}
As a validator, if you want to increase your stake, you will have to delegate to yourself. For delegating to your own validator, `delegator-addr` and `validator-addr` will be the same.
{% endhint %}
