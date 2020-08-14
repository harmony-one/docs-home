# Setting up BLS Keys

## Creating new BLS keys

You will need to generate one or more BLS keys in order to run a validating node. When generating a BLS key, the CLI will ask you to provide a passphrase to encrypt the BLS key file.‌

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

## Configuring the BLS keys

**1.** You need to manually create a folder called `.hmy/blskeys`:

```bash
mkdir -p .hmy/blskeys
```

**2.** Copy all the [previously created BLS key\(s\)](https://docs.harmony.one/home/validators/first-time-setup/generating-a-bls-key) to this new folder:

```bash
cp *.key .hmy/blskeys
```

{% hint style="warning" %}
Make sure all your BLS keys belong to the same shard when using multiple BLS keys. You can use the command below to check each one of them.
{% endhint %}

```bash
./hmy --node="https://api.s0.t.hmny.io" utility shard-for-bls [BLS PUBLIC KEY]
```

**3.** For each BLS key file, a corresponding `<blskey>.pass` file needs to be created inside folder`.hmy/blskeys`with the passphrase inside it.

