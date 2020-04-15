# Changing Validator Information

You can edit your validator’s information using the CLI with the following command.

{% tabs %}
{% tab title="Open Staking Testnet" %}
```bash
./hmy --node="https://api.s0.os.hmny.io" staking edit-validator \
    --validator-addr [ONE ADDRESS] [FIELDS TO EDIT] --passphrase
```
{% endtab %}

{% tab title="Partner Testnet" %}
```bash
./hmy --node="https://api.s0.ps.hmny.io" staking edit-validator \
    --validator-addr [ONE ADDRESS] [FIELDS TO EDIT] --passphrase
```
{% endtab %}
{% endtabs %}

The CLI will prompt you to enter your BLS key file password. Only the `--validator-addr` field is required; all other fields are optional.

* `--validator-addr` is the validator address that you want to edit
* `--active true` to set validator as eligible to be elected
* `--name` to change the name displayed on the Staking Explorer
* `--identity` to change the identity field
* `--website` to change the website field
* `--details` to change the details field
* `--security-contact` to change the security contact field
* `--rate` to change the current commission rate
* `--min-self-delegation` to change the minimum stake by the validator
* `--max-total-delegation` to change the maximum stake that the validator can have
* `--remove-bls-key` to remove a BLS public key associated with your validator
* `--add-bls-key` to add another BLS public key to your validator 

{% hint style="info" %}
`--validator-addr`is the only field that is required.

Sending the command without the arguments will leave those fields of your validator as is.
{% endhint %}

