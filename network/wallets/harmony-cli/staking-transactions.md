# Staking Transactions

## Delegating to a Validator

You can delegate tokens to a validator using the following command:

```bash
./hmy --node="https://api.s0.t.hmny.io" staking delegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \
    --amount [AMOUNT] --passphrase
```

The CLI will ask for the passphrase for the `delegator-addr` keystore file.

`--delegator-addr` is the ONE address of the delegator** (string)**

`--validator-addr` is the ONE address of the validator** (string)**

`--amount` is the number of ONE tokens to delegate to the validator** (float)**

{% hint style="info" %}
As a validator, if you want to increase your stake, you will have to delegate to yourself. For delegating to your own validator, `delegator-addr` and `validator-addr` will be the same.
{% endhint %}

## Undelegating from a Validator

You can un-delegate tokens from a validator using the following command:

```bash
./hmy --node="https://api.s0.t.hmny.io" staking undelegate \
    --delegator-addr [ONE ADDRESS] --validator-addr [ONE ADDRESS] \ 
    --amount [AMOUNT] --passphrase
```

The CLI will ask for the passphrase for the `delegator-addr` keystore file.

`--delegator-addr` is the ONE address of the delegator** (string)**

`--validator-addr` is the ONE address of the validator** (string)**

`--amount` is the number of ONE tokens to un-delegate** (float)**

{% hint style="info" %}
As a validator, for un-delegating from your own validator, `delegator-addr` and `validator-addr` will be the same.
{% endhint %}

## Collecting Rewards

You can collect your block rewards with the following command:

```bash
./hmy --node="https://api.s0.t.hmny.io" staking collect-rewards \
--delegator-addr [ONE ADDRESS] --passphrase
```

The CLI will prompt your for the passphrase of the delegation account.

`--delegator-addr` is the account to collect rewards for

{% hint style="warning" %}
You can only collect ALL of your block rewards at once, not partially.
{% endhint %}
