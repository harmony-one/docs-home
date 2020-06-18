# Generating A BLS Key

## Creating a new BLS key

You will need to generate a BLS key in order to run a validating node. When generating a BLS key, the CLI will ask you to provide a passphrase to encrypt the BLS key file.‌

```bash
./hmy keys generate-bls-keys --count 1 --shard 1 --passphrase
```

On the command above `--count` defines the number of BLS keys you want to generate and `--shard` the shard associated. On this example, we are generating 1 BLS key on shard 1.

{% hint style="danger" %}
Remember your passphrase. You will need it to decrypt the BLS key file in order to create a validator & start a node with that key.

Create a backup of your BLS key file or save the BLS private key \(optional\).
{% endhint %}

{% hint style="info" %}
The BLS public key is the same as the name of the file, without the `.key`.
{% endhint %}

## Checking the BLS key Shard

Optionally, you can check which shard your BLS key is associated with using the command bellow:

```bash
./hmy --node="https://api.s0.t.hmny.io" utility shard-for-bls [BLS PUBLIC KEY]
```

Example output:

```bash
{"shard-id":1}
```

