# Creating new wallet/importing wallet

## New Wallet

Creation of a new account is done as a function of a generated `bip39` mnemonic with 256 bits of entropy. You must provide an account alias name.

```text
./hmy keys add account-name1
```

This creates a keystore at `$(hmy keys location)/account-name1/UTC--2019-09-16T21-25-35.297331000Z--678e7ea3dcb5f4e9724c0e761843572f10c49b73` with a default passphrase of an empty string. The passphrase is used to decrypt the keystore when signing transactions. In case you want to use an alternative passphrase, invoke instead:

```text
./hmy keys add account-name2 --passphrase
```

When creating keys this way, `hmy` will ask you to provide a passphrase.‌ The example-account is just a name you can pick, so pick something simple.  
Make sure you keep track of this passphrase for future use because the passphrase is used to decrypt the keystore when signing transactions. Also make sure you save the seed phrase.

To know where your wallet file has been created, just run the following command:

```text
./hmy keys location
```

The command above will return the location of your wallet file. Backup this wallet file somewhere else.‌

You can check the list of wallets \(local accounts\) with the following command:

```text
./hmy keys list
```

## Import Wallet

### Importing an existing keystore <a id="importing-an-existing-keystore"></a>

‌Sometimes you might have an existing keystore such as keys made by Harmony's `wallet.sh` program. An example:

```text
$ # Note that the shell variable p is an absolute path.
$ p='/Users/edgar/Repos/harmony-work/src/github.com/harmony-one/harmony/.hmy/keystore/one16qsd5ant9v94jrs89mruzx62h7ekcfxmduh2rx.key'
$ hmy keys import ${p}
Imported keystore given account alias of `lecture-imported`
```

‌Keep in mind that you should know the passphrase associated with the imported keystore. For keystores created by Harmony's `wallet.sh`, the default passphrase is an empty string; this matters for signing transactions.‌

NOTE: you can also just move the one16qsd5ant9v94jrs89mruzx62h7ekcfxmduh2rx.key file into the directory where your `hmy` is, then use the command as follows:

```text
./hmy keys import one16qsd5ant9v94jrs89mruzx62h7ekcfxmduh2rx.key 
```

### Importing an existing private key <a id="importing-an-existing-private-key"></a>

Sometimes you might have a secp256k1 private key, such as the one generated from the following command:

```text
openssl ecparam -genkey -name secp256k1 -text -noout -outform DER | xxd -p -c 1000 | sed 's/41534e31204f49443a20736563703235366b310a30740201010420/PrivKey: /' | sed 's/a00706052b8104000aa144034200/\'$'\nPubKey: /'
```

You can import the key with an optional name and passphrase. For example:

```text
./hmy keys import-private-key b8798ca0a56ce16517ea37c6b1229cbb67cf0e022c423b044fe8f537830d8be5 my_wallet_name_here --passphrase myDesiredPassword
```

For clarity, here is the usage \(argument order matters\): 

`./hmy keys import-private-key <secp256k1_PRIVATE_KEY> [ACCOUNT_NAME] [flags]`‌

If no account name is provided, a random word concatenated with `-imported` will be used. If no passphrase is provided, the default passphrase will be used \(which is blank\). Note that the CLI currently only supports importing secp256k1 private keys.

## Recovering a wallet key

You can recover lost wallet keys by entering the mnemonic words you received \(and hopefully saved\) when creating it:

```text
./hmy keys add nameofyourkey --recover
```

