# Collecting Rewards

You can collect your block rewards with the following command.

{% tabs %}
{% tab title="Open Staking Testnet" %}
```text
./hmy --node=https://api.s0.os.hmny.io staking collect-rewards \
--delegator-addr [ONE ADDRESS] --passphrase
```
{% endtab %}

{% tab title="Partner Testnet" %}
```
./hmy --node=https://api.s0.ps.hmny.io staking collect-rewards \
--delegator-addr [ONE ADDRESS] --passphrase
```
{% endtab %}
{% endtabs %}

The CLI will prompt your for the passphrase of the delegation account.

`--delegator-addr` is the account to collect rewards for

{% hint style="warning" %}
You can only collect ALL of your block rewards from all validators.
{% endhint %}

