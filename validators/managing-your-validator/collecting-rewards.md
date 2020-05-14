# Collecting Rewards

You can collect your block rewards with the following command.

## Using the Binary:

```bash
./hmy --node="https://api.s0.t.hmny.io" staking collect-rewards \
--delegator-addr [ONE ADDRESS] --passphrase
```

## Using the Shell Wrapper:

```bash
./hmy.sh -- node="https://api.s0.t.hmny.io" staking collect-rewards \
--delegator-addr [ONE ADDRESS] --passphrase
```

### Example:

```bash
./hmy --node="https://api.s0.t.hmny.io" staking collect-rewards \
--delegator-addr one1km7xg8e3xjys7azp9f4xp8hkw79vm2h3f2lade --passphrase
```

The CLI will prompt your for the passphrase of the delegation account.

`--delegator-addr` is the account to collect rewards for

{% hint style="warning" %}
You can only collect ALL of your block rewards at once, not partially.
{% endhint %}

