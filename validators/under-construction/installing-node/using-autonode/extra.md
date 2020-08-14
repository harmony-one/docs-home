---
description: Some optional extras that you may find useful.
---

# Extra

## Using wallet passphrase from file

We **do not** recommend storing your passphrase in plain text. If you choose to, you can have AutoNode import your wallets passphrase from a file. First, save the passphrase using the following convention:

```text
<ONE-address>.pass
```

Then, move the saved passphrase into the harmony wallet passphrase directory using the following command:

```text
mv ./path/to/<ONE-address>.pass ~/harmony_wallet_pass/<ONE-address>.pass
```

Then, when you run AutoNode with `auto-node run` it will automatically pick up the passphrase.

