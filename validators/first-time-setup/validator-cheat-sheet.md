---
description: Example overall validator flow
---

# Setup Cheatsheet

If you are new to setting up Validators, start [here](validator-cheat-sheet.md).

1. Access your cloud instance.

```bash
ssh -i [KEY].pem [SSH ADDRESS]
```

![AWS Connect Example](../../.gitbook/assets/image%20%2819%29.png)

2. Install `tmux`, if your Linux distribution does not come with it.

```bash
sudo yum install tmux
```

3. Download the Harmony CLI.

```bash
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

4. Create a BLS Key.

```text
./hmy keys generate-bls-key --passphrase
```

5. Download `node.sh`.

```bash
curl -LO https://raw.githubusercontent.com/harmony-one/harmony/master/scripts/node.sh \
&& chmod a+x node.sh
```

6. Start a new `tmux` session called `node`.

```bash
tmux new-session -s node
```

7. Run the node.

{% tabs %}
{% tab title="Open Staking Network" %}
```bash
./node.sh -S -c -z -I -N staking -k [BLS KEY FILE].key
```
{% endtab %}
{% endtabs %}

8. Detach from the tmux session by pressing CTRL and B at the same time, then press D.

9. Check that your node is syncing \(block height &gt; 0\).

```bash
./hmy blockchain latest-header
```

10. Create a new wallet.

```bash
./hmy keys add [ACCOUNT NAME] --passphrase
```

11. Get tokens for your validator.

{% tabs %}
{% tab title="Open Staking Testnet" %}
```bash
curl -X GET https://faucet.os.hmny.io/fund?address=[ONE ADDRESS]
```
{% endtab %}
{% endtabs %}

12. Create your Validator.

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 100000 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name JohnWhitton --identity JohnIdentity --details "John The Validator" \
    --security-contact John --website john@harmony.one \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100000000 --min-self-delegation 100000 --passphrase
```
{% endtab %}
{% endtabs %}

13. Check that your ONE address exists as a validator

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" blockchain validator all | grep [ONE ADDRESS]
```
{% endtab %}
{% endtabs %}

14. Collect rewards

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" staking collect-rewards --delegator-addr [ONE ADDRESS] --passphrase
```
{% endtab %}
{% endtabs %}

15. Check validator information for active flag / availability \(block signed\) / etc ...

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" blockchain validator information [VALIDATOR ONE ADDRESS]
```
{% endtab %}
{% endtabs %}



