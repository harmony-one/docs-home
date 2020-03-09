# Undelegating From A Validator

You can un-delegate tokens from a validator using the following command:

{% tabs %}
{% tab title="Open Staking Testnet" %}
```text
./hmy --node=https://api.s0.os.hmny.io staking undelegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \ 
    --amount [AMOUNT] --passphrase
```
{% endtab %}

{% tab title="Partner Testnet" %}
```
./hmy --node=https://api.s0.ps.hmny.io staking undelegate \
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
For un-delegating to your own validator, `delegator-addr` and `validator-addr` will be the same.
{% endhint %}

## When will I get my tokens back after un-delegating?

When you decide to un-delegate your tokens from a validator on the Open Staking Testnet, your tokens will be subjected to a cooldown period lasting **7 epochs \(~70 minutes\)**. You will receive your tokens back in your account balance on the 8th epoch after an un-delegation transaction.

This means that you **will NOT have access to these tokens and can NOT transfer them for up to 80 minutes** after choosing to un-delegate your tokens from a validator.

