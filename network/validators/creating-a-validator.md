# Creating A Validator

{% hint style="info" %}
Before we proceed, we need to create a new Validator Wallet which will need to funded with 10001 ONE
{% endhint %}

## 1. Creating A New Validator Wallet <a id="new-local-account-creation"></a>

You need to provide a local account name of your choice and provide a passphrase. When creating an account, the CLI will ask you to provide a passphrase to encrypt the keystore file:  
  
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

```bash
./hmy keys list
```

Example output from above command:

```bash
#NAME                                  ADDRESS
example-account1                      one1wh4p0kuc7unxez2z8f82zfnhsg4ty6dupqyjt2
```

### Checking Account Balance

Use the following command to check your balance : **./hmy --node="\[API\_endpoint\]" balances \[ONE ADDRESS\]** ex:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" balances one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd
```
{% endtab %}

{% tab title="Testnet" %}
```bash
./hmy --node="https://api.s0.b.hmny.io" balances one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd
```
{% endtab %}
{% endtabs %}

## 2. Creating a Validator <a id="creating-a-validator"></a>

{% hint style="info" %}
For you to create a Validator successfully, it needs to have 10000 ONE tokens plus the necessary fees to create the validator transaction on chain. For this reason, we recommend that you send at least 10001 ONE tokens to your `--validator-addr`before you continue.

For Testnet tokens, check [here](../../developers/network-and-faucets.md#faucets).
{% endhint %}

Replace everything in \[ \] with your own data:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 10000 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name "[NAME]" --identity "[IDENTITY]" --details "DETAILS" \
    --security-contact "CONTACT" --website "YOUR-WEBSITE.COM" \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100000000 --min-self-delegation 10000 --passphrase
```
{% endtab %}

{% tab title="Testnet" %}
```bash
./hmy --node="https://api.s0.b.hmny.io" staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 10000 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name "[NAME]" --identity "[IDENTITY]" --details "DETAILS" \
    --security-contact "CONTACT" --website "YOUR-WEBSITE.COM" \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100000000 --min-self-delegation 10000 --passphrase
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Copy the entire command. **Extra white spaces in the command could cause errors.**

Name, identity, details, security-contact and website need to be put in double quotes if there are more than one word separated by space \(example --name "John the validator"\).
{% endhint %}

The CLI will prompt you to enter your BLS key file password.

`--validator-addr` is the validator ONE address **\(string\)**

`--amount` is the initial amount of ONE you want to stake **\(float\)**

`--bls-pubkeys` takes a comma-separated list of BLS public keys **\(string\)**

`--name` will be the name displayed on the Staking Explorer **\(string\)**

`--identity` unique identifier for the validator **\(string\)**

`--details` is the description of the validator **\(string\)**

`--security-contact` is security contact for the validator **\(string\)**

`--website` will be the website displayed on the Staking Explorer **\(string\)**

`--max-change-rate` is the maximum rate change the validator can do to their commission rate every epoch **\(float\)**

`--max-rate` is the maximum commission rate that the validator can set **\(float\)**

`--rate` is the commission rate of the validator **\(float\)**

`--max-total-delegation` is the maximum amount of ONE that can be delegated to this validator **\(float\)**

`--min-self-delegation` is the minimum amount of ONE the validator must stake to itself **\(float\)**

{% hint style="danger" %}
`--max-rate` and `--max-change-rate` cannot be changed later.

`--min-self-delegation` has to be at least 10,000 ONE.
{% endhint %}

{% hint style="info" %}
`--rate`, `--max-rate`, and `--max-change-rate` accepts numbers between 0 and 1 representing percentages
{% endhint %}

{% hint style="info" %}
If you have a Keybase account, we recommend you use your [Keybase public key fingerprint ](managing-a-validator/adding-a-validator-logo.md#using-keybase-recommended)as your validator's identity. The field is unique, ensuring that other validator's can not attempt to impersonate you. This data will also help with some awesome integrations & features in the future!
{% endhint %}

