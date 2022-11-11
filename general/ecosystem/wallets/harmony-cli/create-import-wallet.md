# Create or Import Wallet

{% hint style="info" %}
When we mention the binary, we are referencing the `./hmy` binary from the [setup procedure](download-setup.md#1-for-linux-pure-statically-linked-binary).

When we mention the shell scripts, we are referencing the `./hmy.sh` shell script from the [setup procedure.](download-setup.md#2-for-macos-dynamically-linked-binary)
{% endhint %}

## New Wallet

{% hint style="info" %}
Creation of a new account is done as a function of a generated `bip39` mnemonic with 256 bits of entropy. You must provide an account alias name.
{% endhint %}

### Using the Binary:

```bash
./hmy keys add <account-name> [--passphrase]
```

### Using the Shell Wrapper:

```bash
./hmy.sh -- keys add <account-name1> [--passphrase]
```

### Example:

```bash
./hmy keys add test-account --passphrase
```

{% hint style="warning" %}
Write/store this seed phrase in a safe place. it is the only way to recover your account if you ever forget your password.
{% endhint %}

This creates a keystore at the following directory:`(hmy keys location)/account-name1/UTC--2019-09-16T21-25-35.297331000Z--678e7ea3dcb5f4e9724c0e761843572f10c49b73`

When creating keys this way, `hmy` will ask you to provide a passphrase.‌ Make sure you keep track of this passphrase for future use because the passphrase is used to decrypt the keystore when signing transactions. Also make sure you save the seed phrase, also called a mnemonic.

{% hint style="info" %}
If you don't provide a passphrase using the `--passphrase` flag, the default passphrase is an empty string `""`. The passphrase is used to decrypt the keystore when signing transactions.
{% endhint %}

To know where your wallet file has been created, run the following command:

#### Using the Binary:

```bash
./hmy keys location
```

#### Using the Shell Wrapper:

```bash
./hmy.sh -- keys location
```

You can check the list of wallets (local accounts) with the following command:

#### Using the Binary:

```bash
./hmy keys list
```

#### Using the Shell Wrapper:

```bash
./hmy.sh -- keys list
```

## Import Wallet

### Importing a Keystore <a href="importing-an-existing-keystore" id="importing-an-existing-keystore"></a>

‌You might have an existing keystore made by Harmony's old `wallet.sh` program that ends with ".key" in the file name (example):

`one16qsd5ant9v94jrs89mruzx62h7ekcfxmduh2rx.key`

Or that starts with "UTC" in the file name (example):

`UTC--2020-01-15T01-02-06.606670000Z--9689a0711642bf08ea92ed98d552f0c1b8c8cefb`

Both these files can be imported into `hmy` using the command `import-ks` as shown below.

{% hint style="warning" %}
Note that the --passphrase flag only enables a password prompt after the command is entered, there are no other arguments necessary here (if you dont put --passphrase flag in the command it will assume no password needed and will not prompt you for one, which basically means that your wallet keyfile will not be password protected!).
{% endhint %}

#### Using the Binary:

```bash
./hmy keys import-ks <absolute_path_to_keystore> --passphrase
```

#### Using the Shell Script:

```bash
./hmy.sh -- keys import-ks <absolute_path_to_keystore> --passphrase
```

#### Examples:

```bash
./hmy keys import-ks /home/harmony/one16qsd5ant9v94jrs89mruzx62h7ekcfxmduh2rx.key --passphrase
./hmy keys import-ks /home/harmony/UTC--2020-01-15T01-02-06.606670000Z--9689a0711642bf08ea92ed98d552f0c1b8c8cefb --passphrase
```

‌Keep in mind that you should know the passphrase associated with the imported keystore and pass it as a parameter as shown in the commands above. For keystores created by Harmony's `wallet.sh`, the default passphrase is an empty string; this matters for signing transactions.‌

### Importing a Private Key <a href="importing-an-existing-private-key" id="importing-an-existing-private-key"></a>

Sometimes you might have a secp256k1 private key, such as the one generated from the following command:

```bash
openssl ecparam -genkey -name secp256k1 -text -noout -outform DER | xxd -p -c 1000 | sed 's/41534e31204f49443a20736563703235366b310a30740201010420/PrivKey: /' | sed 's/a00706052b8104000aa144034200/\'$'\nPubKey: /'
```

You can import the key with an optional name and passphrase

#### Using the Binary:

```bash
./hmy keys import-private-key <secp256k1_private_key> [wallet_name] [--passphrase]
```

#### Using the Shell Script:

```bash
./hmy.sh -- keys import-private-key <secp256k1_private_key> [wallet_name] [--passphrase]
```

#### Example:

```bash
./hmy keys import-private-key b8798ca0a56ce16517ea37c6b1229cbb67cf0e022c423b044fe8f537830d8be5 my_wallet_name_here --passphrase
```

If no account name is provided, a random word concatenated with `-imported` will be used. If no passphrase is provided, the default passphrase will be used (which is blank). Note that the CLI currently only supports importing secp256k1 private keys.

### Importing a Mnemonic Phrase <a href="importing-an-existing-mnemonic-phrase" id="importing-an-existing-mnemonic-phrase"></a>

You can recover lost wallet keys by entering the mnemonic words you received (and hopefully saved) when creating it:

#### Using the Binary:

```bash
./hmy keys recover-from-mnemonic [wallet_name]
```

#### Using the Shell Script:

```bash
./hmy.sh -- keys recover-from-mnemonic [wallet_name]
```

#### Example:

```bash
./hmy keys recover-from-mnemonic nameofyourkey
```
