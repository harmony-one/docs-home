---
description: Example overall alidator flow
---

# Validator Cheat Sheet

If you are new to setting up Validators, start [here](validator-cheat-sheet.md).

1. Access your cloud instance.

```text
ssh -i [KEY].pem [SSH ADDRESS]
```

![AWS Connect Box](../.gitbook/assets/image%20%285%29.png)

2. Update software & install `tmux`

```text
sudo yum update && sudo yum install tmux
```

3. Download the Harmony CLI.

```text
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

4. Create a BLS Key

```text
./hmy keys generate-bls-key --passphrase
```

5. Download `node2.sh`

```text
curl -LO https://harmony.one/node2.sh && mv node2.sh node.sh && chmod a+x node.sh
```

6. Start a new `tmux` session called `node`

```text
tmux new -s node
```

7. Run the node

```text
./node.sh -S -N staking -z -k [BLS KEY FILE].key
```

8. Detach from the tmux session by pressing CTRL and B at the same time, then press D.

9. Check that your node is syncing \(block height &gt; 0\)

```text
./hmy blockchain latest-header
```

10. Create a wallet

```text
./hmy keys add [ACCOUNT NAME] --passphrase
```

{% hint style="info" %}
Use `./hmy keys list` to get your ONE address.
{% endhint %}

11. Get tokens for your validator

{% tabs %}
{% tab title="Open Staking Testnet" %}
```text
curl -X GET https://faucet.os.hmny.io/fund?address=[ONE ADDRESS]
```
{% endtab %}

{% tab title="Partner Testnet" %}
```
curl -X GET https://faucet.ps.hmny.io/fund?address=[ONE ADDRESS]
```
{% endtab %}
{% endtabs %}

12. Create your Validator

{% tabs %}
{% tab title="Open Staking Testnet" %}
```text
./hmy --node="https://api.s0.os.hmny.io" staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 10 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name JohnWhitton --identity JohnIdentity --details "John The Validator" \
    --security-contact John --website john@harmony.one \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100 --min-self-delegation 10 --passphrase
```
{% endtab %}

{% tab title="Partner Testnet" %}
```
./hmy --node="https://api.s0.ps.hmny.io" staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 10 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name JohnWhitton --identity JohnIdentity --details "John The Validator" \
    --security-contact John --website john@harmony.one \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100 --min-self-delegation 10 --passphrase
```
{% endtab %}
{% endtabs %}

13. Check that your ONE address exists as a validator

{% tabs %}
{% tab title="Open Staking Testnet" %}
```text
./hmy --node="https://api.s0.os.hmny.io" blockchain validator all | grep [ONE ADDRESS]
```
{% endtab %}

{% tab title="Partner Testnet" %}
```
./hmy --node="https://api.s0.ps.hmny.io" blockchain validator all | grep [ONE ADDRESS]
```
{% endtab %}
{% endtabs %}

14. Collect rewards

{% tabs %}
{% tab title="Open Staking Testnet" %}
```text
./hmy --node="https://api.s0.os.hmny.io" staking collect-rewards --delegator-addr [ONE ADDRESS]
```
{% endtab %}

{% tab title="Partner Testnet" %}
```
./hmy --node="https://api.s0.ps.hmny.io" staking collect-rewards --delegator-addr [ONE ADDRESS]
```
{% endtab %}
{% endtabs %}

15. Check validator information for active flag / availability \(block signed\) / etc ...

{% tabs %}
{% tab title="Open Staking Testnet" %}
```
./hmy --node="https://api.s0.os.hmny.io" validator information [VALIDATOR ONE ADDRESS]
```
{% endtab %}

{% tab title="Partner Testnet" %}
```
./hmy --node="https://api.s0.ps.hmny.io" validator information [VALIDATOR ONE ADDRESS]
```
{% endtab %}
{% endtabs %}



