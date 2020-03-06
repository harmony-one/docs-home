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

1. Update software & install `tmux`

```text
sudo yum update && sudo yum install tmux
```

1. Download the Harmony CLI.

```text
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

1. Create a BLS Key

```text
./hmy keys generate-bls-key --passphrase
```

1. Download `node2.sh`

```text
curl -LO https://harmony.one/node2.sh && mv node2.sh node.sh && chmod a+x node.sh
```

1. Start a new `tmux` session called `node`

```text
tmux new -s node
```

1. Run the node

```text
./node.sh -S -N staking -z -k [BLS KEY FILE].key
```

1. Detach from the tmux session by pressing CTRL and B at the same time, then press D.
2. Check that your node is syncing \(block height &gt; 0\)

```text
./hmy blockchain latest-header
```

1. Create a wallet

```text
./hmy keys add [ACCOUNT NAME] --passphrase
```

{% hint style="info" %}
Use `./hmy keys list` to get your ONE address.
{% endhint %}

1. Get tokens for your validator

```text
curl -X GET https://faucet.os.hmny.io/fund?address=[ONE ADDRESS]
```

1. Create your Validator

```text
./hmy --node="https://api.s0.os.hmny.io" staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 10 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name JohnWhitton --identity JohnIdentity --details "John The Validator" \
    --security-contact John --website john@harmony.one \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100 --min-self-delegation 10 --passphrase
```

1. Check that your ONE address exists as a validator

```text
./hmy --node="https://api.s0.os.hmny.io" blockchain validator all | grep [ONE ADDRESS]
```

1. Collect rewards

```text
./hmy --node="https://api.s0.os.hmny.io" staking collect-rewards --delegator-addr [ONE ADDRESS]
```

