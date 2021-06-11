---
description: How to undelegate your tokens from a validator
---

# Undelegating From A Validator

You can un-delegate tokens from a validator using the following command:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" staking undelegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \ 
    --amount [AMOUNT] --passphrase
```
{% endtab %}

{% tab title="Testnet" %}
```bash
./hmy --node="https://api.s0.b.hmny.io" staking undelegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \ 
    --amount [AMOUNT] --passphrase
```
{% endtab %}
{% endtabs %}

## Example:

```bash
./hmy.sh -- node="https://api.s0.t.hmny.io" staking undelegate \
    --delegator-addr one1km7xg8e3xjys7azp9f4xp8hkw79vm2h3f2lade --validator-addr one1km7xg8e3xjys7azp9f4xp8hkw79vm2h3f2lade \ 
    --amount 10000 --passphrase
```

The CLI will ask for the passphrase for the `delegator-addr` keystore file.

`--delegator-addr` is the ONE address of the delegator **\(string\)**

`--validator-addr` is the ONE address of the validator **\(string\)**

`--amount` is the number of ONE tokens to un-delegate **\(float\)**

{% hint style="info" %}
As a validator, for un-delegating from your own validator, `delegator-addr` and `validator-addr` will be the same.
{% endhint %}

## When will I get my tokens back after un-delegating?

When you decide to un-delegate your tokens from a validator, your tokens will be released at the end of the epoch from when you un-delegate.

This means that you **will NOT have access to these tokens and can NOT transfer them** after choosing to un-delegate your tokens from a validator until the tokens are in your account.

If your validator didn't get elected in the last epoch, you will get the token back at the end of current epoch.

