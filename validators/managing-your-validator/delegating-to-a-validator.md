# Delegating To A Validator

You can delegate tokens to a validator using the following command.

{% tabs %}
{% tab title="Open Staking Testnet" %}
```text
./hmy --node=https://api.s0.os.hmny.io staking delegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \
    --amount [AMOUNT] --passphrase
```
{% endtab %}

{% tab title="Partner Testnet" %}
```
./hmy --node="https://api.s0.ps.hmny.io" staking delegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \
    --amount [AMOUNT] --passphrase
```
{% endtab %}
{% endtabs %}

The CLI will ask for the passphrase for the `delegator-addr` keystore file.

`--delegator-addr` is the ONE address of the delegator

`--validator-addr` is the ONE address of the validator

`--amount` is the number of ONE tokens to un-delegate

{% hint style="info" %}
If you want to increase your stake, you will have to delegate to yourself. For delegating to your own validator, `delegator-addr` and `validator-addr` will be the same.
{% endhint %}

