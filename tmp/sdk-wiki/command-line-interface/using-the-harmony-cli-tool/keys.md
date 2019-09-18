---
description: Explanations & usage of the keys subcommand
---

# Keys

### Available actions

Here is the top level entry point of the `keys` subcommand for `hmy_cli`

```text
$ hmy_cli keys

Manage your local keys

Usage:
  hmy_cli keys [flags]
  hmy_cli keys [command]

Available Commands:
  add         Create a new key with passphrase
  delete      Delete the given key
  list        List all keys
  mnemonic    Compute the bip39 mnemonic for some input entropy
  show        Show key info for the given name
  update      Change the password used to protect private key

Flags:
  -h, --help   help for keys

Global Flags:
  -p, --pretty   pretty print JSON outputs

Use "hmy_cli keys [command] --help" for more information about a command.
```

As you can see, the `keys` subcommand is very important because it the entrypoint for managing your Harmony accounts \(keys\).

### Key creation

TODO expand out



