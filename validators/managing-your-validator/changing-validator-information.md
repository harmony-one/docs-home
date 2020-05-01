# Changing Validator Information

You can edit your validator’s information using the CLI with the following command.

{% tabs %}
{% tab title="Open Staking Testnet" %}
```bash
./hmy --node="https://api.s0.os.hmny.io" staking edit-validator \
    --validator-addr [ONE ADDRESS] [FIELDS TO EDIT] --passphrase
```
{% endtab %}
{% endtabs %}

The CLI will prompt you to enter your BLS key file password. Only the `--validator-addr` field is required; all other fields are optional.

* `--validator-addr` is the validator ONE address that you want to edit **\(string\)**
* `--active` to set validator as eligible or not to be elected **\(bool\)**
* `--name` to change the name displayed on the Staking Explorer **\(string\)**
* `--identity` to change the identity field **\(string\)**
* `--website` to change the website field **\(string\)**
* `--details` to change the details field **\(string\)**
* `--security-contact` to change the security contact field **\(string\)**
* `--rate` to change the current commission rate **\(float\)**
* `--min-self-delegation` to change the minimum stake by the validator **\(float\)**
* `--max-total-delegation` to change the maximum stake that the validator can take **\(float\)**
* `--remove-bls-key` to remove a BLS public key associated with your validator **\(string\)**
* `--add-bls-key` to add another BLS public key to your validator **\(string\)**

{% hint style="info" %}
`--validator-addr`is the only field that is required.

Sending the command without the arguments will leave those fields of your validator as is.
{% endhint %}

{% hint style="danger" %}
`--max-rate` and `--max-change-rate` cannot be changed later.

`--min-self-delegation` has to be at least 10,000 ONE.
{% endhint %}

