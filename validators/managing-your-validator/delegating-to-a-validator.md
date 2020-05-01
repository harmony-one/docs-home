# Delegating To A Validator

You can delegate tokens to a validator using the following command.

{% tabs %}
{% tab title="Open Staking Testnet" %}
```bash
./hmy --node="https://api.s0.os.hmny.io" staking delegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \
    --amount [AMOUNT] --passphrase
```
{% endtab %}
{% endtabs %}

The CLI will ask for the passphrase for the `delegator-addr` keystore file.

`--delegator-addr` is the ONE address of the delegator **\(string\)**

`--validator-addr` is the ONE address of the validator **\(string\)**

`--amount` is the number of ONE tokens to delegate to the validator **\(float\)**

{% hint style="info" %}
As a validator, if you want to increase your stake, you will have to delegate to yourself. For delegating to your own validator, `delegator-addr` and `validator-addr` will be the same.
{% endhint %}

