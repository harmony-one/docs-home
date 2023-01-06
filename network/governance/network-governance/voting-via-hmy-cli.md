# Voting via HMY CLI

Make sure to read the introduction and rules [here](./) first.&#x20;

To install HMY CLI head [here](../../../general/wallets/harmony-cli/).

For a complete reference on all available commands for governance:

```bash
./hmy governance --help
```

### Vote on Proposal

```bash
./hmy governance vote-proposal --proposal=QmdmnVwW6ob5UfB9hNYxKsRXAyM52jQpNXsV5Vw4fNbiqa --choice=agree --key=key-name
```

key is the key name of your validator imported via hmy and available in `./hmy keys list`

