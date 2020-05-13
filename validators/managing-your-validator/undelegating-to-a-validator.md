# Undelegating From A Validator

You can un-delegate tokens from a validator using the following command:

## Using the Binary:

```bash
./hmy --node="<endpoint-address>" staking undelegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \ 
    --amount [AMOUNT] --passphrase
```

## Using the Shell Wrapper:

```bash
./hmy.sh -- node="<endpoint-address>" staking undelegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \ 
    --amount [AMOUNT] --passphrase
```

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

When you decide to un-delegate your tokens from a validator, your tokens will be subjected to a cool-down period lasting **7 epochs**. You will receive your tokens back in your account balance on the 8th epoch after an un-delegation transaction. 

This means that you **will NOT have access to these tokens and can NOT transfer them** after choosing to un-delegate your tokens from a validator.

If your validator didn't get elected in the last 7 epoch, there is no cool-down period and you will get the token back at the end of current epoch.

