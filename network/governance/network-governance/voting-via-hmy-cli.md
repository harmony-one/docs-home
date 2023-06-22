# Voting via HMY CLI

Make sure to read the introduction and rules [here](./) first.&#x20;

To install HMY CLI head [here](../../../general/wallets/harmony-cli/).

For a complete reference on all available commands for governance:

```bash
./hmy governance --help
```

### Vote on Proposal

{% code fullWidth="false" %}
```bash
Yes
./hmy governance vote-proposal --proposal=<replace-with-propose-0x-hash> --choice=1 --node="https://api.s0.t.hmny.io" --key=<replace-with-your-local-key-name> --passphrase

No
./hmy governance vote-proposal --proposal=<replace-with-propose-0x-hash> --choice=2 --node="https://api.s0.t.hmny.io" --key=<replace-with-your-local-key-name> --passphrase

Abstain
./hmy governance vote-proposal --proposal=<replace-with-propose-0x-hash> --choice=3 --node="https://api.s0.t.hmny.io" --key=<replace-with-your-local-key-name> --passphrase
```
{% endcode %}

key is the key name of your validator imported via hmy and available in `./hmy keys list`

