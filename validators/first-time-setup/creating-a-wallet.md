# Creating A Wallet

## New Wallet \(CLI\) <a id="new-local-account-creation"></a>

You need to provide a local account name of your choice and provide a passphrase. _\*\*_When creating an account, the CLI will ask you to provide a passphrase to encrypt the keystore file :  
**./hmy keys add \[LOCAL ACCOUNT NAME\] --passphrase**  example : 

```text
./hmy keys add mylocalaccountname --passphrase
```

{% hint style="danger" %}
Remember your passphrase. You will need it to decrypt the account keystore in order to send transactions & perform other actions.

Also save your seed phrase \(mnemonic\) somewhere as well, in case you lose your keystore.
{% endhint %}

### Backing Up Your Keystore File \(Optional\)

```text
./hmy keys location
```

The command above will return the location of your account keystore. You may want to create a backup of this file.‌

You can check the list of wallets \(local accounts\) with the following command:

```text
./hmy keys list
```

Example output from above command:

```text
NAME                                  ADDRESS

example-account1                      one1wh4p0kuc7unxez2z8f82zfnhsg4ty6dupqyjt2
```

## Helpful Information

### Checking your account balance

If you are running a node and your node is synced to the latest block, use the following command to check your balance : **./hmy balances \[ONE ADDRESS\]** ex:

```text
./hmy balances one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd
```

If you are not running a node or your node is not synced, use the following command to check your balance : **./hmy --node="\[API\_endpoint\]" balances \[ONE ADDRESS\]** ex:

{% tabs %}
{% tab title="Open Staking Testnet" %}
```bash
./hmy --node="https://api.s0.os.hmny.io" balances one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd
```
{% endtab %}

{% tab title="Partner Testnet" %}
```bash
./hmy --node="https://api.s0.ps.hmny.io" balances one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd
```
{% endtab %}
{% endtabs %}

