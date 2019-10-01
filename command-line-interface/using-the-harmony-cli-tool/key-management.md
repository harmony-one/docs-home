---
description: 'Managing accounts & their keys on your local machine, hardware wallets'
---

# Key management

As of commit `521aa050e479d3032d7f1f83468650b48aa5f613`, `hmy` provides two ways of helping you managing accounts and keys.

1. On the local machine where the `hmy` binary runs, you can see where `hmy` keeps track of accounts and keys by invoking `$ hmy keys location`
2. On a hardware Ledger Nano S

You can check the local accounts like so:

```text
$ hmy keys list
NAME                                                ADDRESS

acc3                                                one1wh4p0kuc7unxez2z8f82zfnhsg4ty6dupqyjt2
advance                                             one16qsd5ant9v94jrs89mruzx62h7ekcfxmduh2rx
sort-imported                                       one1658znfwf40epvy7e46cqrmzyy54h4n0qa73nep
visual-imported                                     one12fuf7x9rgtdgqg7vgq0962c556m3p7afsxgvll
```

The `NAME` column does not correspond to anything outside of your local machine, it is merely an artifact of the way that `hmy` organizes your keys.

```text
$ accts=$(hmy keys location)
$ cd ${accts}
$ tree
.
├── acc3
│   └── UTC--2019-09-10T03-08-29.324445105Z--75ea17db98f7266c89423a4ea12677822ab269bc
├── advance
│   └── UTC--2019-09-14T22-39-10.606297000Z--d020da766b2b0b590e072ec7c11b4abfb36c24db
├── sort-imported
│   └── UTC--2019-09-15T00-29-16.692667000Z--d50e29a5c9abf21613d9aeb001ec44252b7acde0
└── visual-imported
    └── UTC--2019-09-15T00-23-19.135443000Z--52789f18a342da8023cc401e5d2b14a6b710fba9

4 directories, 4 files
```

Thus the name of a directory in `accts` is the name of an account alias and the contents of a directory in `accts` is an encrypted keystore.

## New local account creation

### Plain case

Creation of a new account is done as a function of a generated `bip39` mnemonic with 256 bits of entropy. You must provide an account alias name.

```text
$ hmy keys add example-account
**Important** write this seed phrase in a safe place, it is the only way to recover your account if you ever forget your password

already memory moral any much letter forum odor never vintage text judge apology manual oyster double dragon barely rain supply sunset more donate afford
```

This creates a keystore at `$(hmy keys location)/example-account/TC--2019-09-16T21-25-35.297331000Z--678e7ea3dcb5f4e9724c0e761843572f10c49b73` with a default passphrase of `harmony-one`. The passphrase is used to decrypt the keystore when signing transactions. In case you want to use an alternative passphrase, invoke instead:

```text
$ hmy keys add throw-away-acc1 --passphrase
Enter passphrase for account
Repeat the passphrase:
```

When creating keys this way, `hmy` will ask you to provide a passphrase without repeating it on the screen.

### Importing an existing keystore

Sometimes you might have an existing keystore such as keys made by Harmony's `wallet.sh` program. An example:

```text
$ # Note that the shell variable p is an absolute path.
$ p='/Users/edgar/Repos/harmony-work/src/github.com/harmony-one/harmony/.hmy/keystore/one16qsd5ant9v94jrs89mruzx62h7ekcfxmduh2rx.key'
$ hmy keys import ${p}
Imported keystore given account alias of `lecture-imported`
```

Keep in mind that you should know the passphrase associated with the imported keystore. For keystores created by Harmony's `wallet.sh`, the default passphrase is an empty string; this matters for signing transactions.

### Importing an existing private key

Sometimes you might have a secp256k1 private key, such as the one generated from the following command:

```text
$ openssl ecparam -genkey -name secp256k1 -text -noout -outform DER | xxd -p -c 1000 | sed 's/41534e31204f49443a20736563703235366b310a30740201010420/PrivKey: /' | sed 's/a00706052b8104000aa144034200/\'$'\nPubKey: /'
```

You can import the key with an optional name and passphrase. For example:

```text
$ hmy keys import-private-key b8798ca0a56ce16517ea37c6b1229cbb67cf0e022c423b044fe8f537830d8be5 my_name_here --passphrase
```

For clarity, here is the usage \(argument order matters\): `hmy keys import-private-key <secp256k1_PRIVATE_KEY> [ACCOUNT_NAME] [flags]`

If no account name is provided, a random word concatenated with `-imported` will be used.  
If no passphrase is provided, the default passphrase will be used \(which is `harmony-one`\).  
Note that the CLI currently only supports importing secp256k1 private keys.

