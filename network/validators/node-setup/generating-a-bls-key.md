# 2. Setting up BLS Keys

## Creating new BLS keys

You will need to generate one or more BLS keys in order to run a validating node. When generating a BLS key, the CLI will ask you to provide a passphrase to encrypt the BLS key file.‌

```bash
./hmy keys generate-bls-keys --count 1 --shard 1 --passphrase
```

On the command above `--count` defines the number of BLS keys you want to generate and `--shard` the shard associated. On this example, we are generating 1 BLS key on shard 1.

{% hint style="danger" %}
Remember your passphrase. You will need it to decrypt the BLS key file in order to create a validator & start a node with that key.

Create a backup of your BLS key file or save the BLS private key (optional).
{% endhint %}

{% hint style="info" %}
The BLS public key is the same as the name of the file, without the `.key`.
{% endhint %}

## Configuring the BLS keys

**1.** You need to manually create a folder called `.hmy/blskeys`:

```bash
mkdir -p .hmy/blskeys
```

**2.** Copy all the [previously created BLS key(s)](https://docs.harmony.one/home/validators/first-time-setup/generating-a-bls-key) to this new folder:

```bash
cp *.key .hmy/blskeys
```

{% hint style="warning" %}
Make sure all your BLS keys belong to the same shard when using multiple BLS keys. You can use the command below to check each one of them.
{% endhint %}

```bash
./hmy --node="https://api.s0.t.hmny.io" utility shard-for-bls [BLS PUBLIC KEY]
```

{% hint style="danger" %}
Please double check the last digit for your bls key until v2025.0.1 release with [fix(PR-4566)](https://github.com/harmony-one/harmony/pull/4566) will be created:

* shard 0 make sure the last character ends with 0, 4, 8, c
* shard 1 make sure the last character ends with 1, 5, 9, d
{% endhint %}

**3.** For each BLS key file, a corresponding `<blskey>.pass` file needs to be created inside folder`.hmy/blskeys`with the passphrase inside it.

following this format :

```bash
echo '[replace_with_your_passphrase]' > .hmy/blskeys/[replace_with_BLS_without_.key].pass
```

you should finally have in your .hmy/blskeys folder :

```bash
ls .hmy/blskeys/
0c8a92c872798742031c612acea7b686a58b16722a02e072442f14ad4f9499e934da97f4db7d1a68307a96335e06bb0c.key
0c8a92c872798742031c612acea7b686a58b16722a02e072442f14ad4f9499e934da97f4db7d1a68307a96335e06bb0c.pass
```

## Setting up a standby node with the same BLS key is forbidden

{% hint style="danger" %}
It is forbidden now to run multiple nodes using the same set of BLS keys. As we are moving towards full decentralization, external validators will become the shard leader and start to propose blocks. If one validator runs multiple nodes using the same set of valid keys, they may all become valid leaders when the key is rotated to this validator, in this case, the blockchain is experiencing a high risk of hard-fork as different valid leaders may propose different blocks. So, do not run redundant validator nodes anymore on the Harmony blockchain. This is also strictly forbidden on all PoS blockchains such as Ethereum 2, Cosmos.
{% endhint %}

