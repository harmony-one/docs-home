---
description: Explanations & usage of the keys subcommand
---

# Keys

## Available actions

### Create a new key with passphrase

In this example, "qwerty" is the passphrase used to secure the private key.

```bash
$ hc keys add -w "qwerty"
account: one1jdmpflseduxxvga0dz20ewtnamn8x0jyhfphu4
URL: keystore:///Users/suneel/.hmy_cli/keystore/UTC--2019-09-09T17-33-44.327829000Z--937614fe196f0c6623af6894fcb973eee6733e44
```

### Delete a given key

Not Implemented.

### List all keys

```bash
$ hc keys list
Harmony Address:                                         File URL:
one1laankhgq8ual2yqejc295cvycdlntgy09p228p         keystore:///Users/suneel/.hmy_cli/keystore/UTC--2019-09-09T17-32-05.995003000Z--ff7b3b5d003f3bf5101996145a6184c37f35a08f
one1jdmpflseduxxvga0dz20ewtnamn8x0jyhfphu4         keystore:///Users/suneel/.hmy_cli/keystore/UTC--2019-09-09T17-33-44.327829000Z--937614fe196f0c6623af6894fcb973eee6733e44
```

### Compute a bip39 mnemonic from some input entropy

Not Implemented.

### Show key info for a given name

Not Implemented.

### Change the password used to protect a private key

Not Implemented.

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

## Key creation

TODO expand out

