# Undelegating From A Validator

You can un-delegate tokens from a validator using the following command:

{% tabs %}
{% tab title="Open Staking Testnet" %}
```bash
./hmy --node="https://api.s0.os.hmny.io" staking undelegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \ 
    --amount [AMOUNT] --passphrase
```
{% endtab %}

{% tab title="Partner Testnet" %}
```bash
./hmy --node="https://api.s0.ps.hmny.io" staking undelegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \ 
    --amount [AMOUNT] --passphrase
```
{% endtab %}
{% endtabs %}

The CLI will ask for the passphrase for the `delegator-addr` keystore file.

`--delegator-addr` is the ONE address of the delegator **\(string\)**

`--validator-addr` is the ONE address of the validator **\(string\)**

`--amount` is the number of ONE tokens to un-delegate **\(float\)**

{% hint style="info" %}
As a validator, for un-delegating from your own validator, `delegator-addr` and `validator-addr` will be the same.
{% endhint %}

## When will I get my tokens back after un-delegating?

When you decide to un-delegate your tokens from a validator on the Open Staking Testnet, your tokens will be subjected to a cool-down period lasting **7 epochs \(~70 minutes\)**. You will receive your tokens back in your account balance on the 8th epoch after an un-delegation transaction. 

This means that you **will NOT have access to these tokens and can NOT transfer them for up to 80 minutes** after choosing to un-delegate your tokens from a validator.

If your validator didn't get elected in the last 7 epoch, there is no cool-down period and you will get the token back at the end of current epoch.

