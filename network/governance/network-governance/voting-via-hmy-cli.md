# Voting via HMY CLI

Make sure to read the introduction and rules [here](./) first.&#x20;

To install HMY CLI head [here](../../../general/ecosystem/wallets/harmony-cli/).

For a complete reference on all available commands for governance:

```bash
./hmy governance --help
```

### List Spaces

```bash
./hmy governance list-space
```

Output example:

```
        KEY       | NETWORK |      NAME
------------------+---------+------------------
  staking-mainnet |       1 | Harmony Mainnet
  staking-testnet |       2 | Harmony Testnet
```

### List Proposals

```bash
./hmy governance list-proposal --space=staking-mainnet
```

### View Proposal

```bash
./hmy governance view-proposal --proposal=QmdmnVwW6ob5UfB9hNYxKsRXAyM52jQpNXsV5Vw4fNbiqa
```

### Vote on Proposal

```bash
./hmy governance vote-proposal --proposal=QmdmnVwW6ob5UfB9hNYxKsRXAyM52jQpNXsV5Vw4fNbiqa --choice=agree --key=key-name
```

key is the key name of your validator imported via hmy and available in `./hmy keys list`

### New Proposal

```bash
./hmy governance new-proposal --proposal-yaml proposal.yaml --key=key-name
```

For the `proposal.yaml` file, you can use the template below. Change it accordingly:

```bash
space: staking-mainnet
start: 2020-04-16 21:45:12
end: 2020-04-21 21:45:12
choices:
  - agree
  - disagree
title: MyTytle
body: |
  Add here the body text
```

{% hint style="info" %}
**Start** and **end** time is in UTC, Time Zone (Coordinated Universal Time).
{% endhint %}
