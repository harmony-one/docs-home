# 2. Setting up BLS Keys

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
##Setting up a redundant node with the same BLS key

As previously mentioned, Harmony allows you to run 2 nodes with the same BLS key and it is not considered double signing.

In order to run a redunant node (a node with the same BLS key) you need to do the following:

**1.** Copy the BLS .key file onto your local machine from the VPS using the `scp` command.
**2.** Copy the BLS .key from your local machine to the other VPS where you will be running the redunant node on using the `scp` command. Here is a helpful video to guide you through the `scp` process - [guide](https://www.youtube.com/watch?v=q2OHvlr081s)
**3.** You can now follow the same configuration steps as you did above (making a folde called `.hmy/blskeys`, copying the BLS key into this new folder, etc.)
**4.** After you followed the same configuration steps for the BLS key, you can move on and follow the exact same steps for syncing the database and installing the node.

{% hint style="warning" %}
If your redunant node doesn't work properly (e.g. daemon process stops) after you followed all the steps, check the .pass file that you created. The passphrase inside it might have been copied incorrectly with the `echo` command.
If that happens, use a text editor and edit the file manually and input your passphrase.
You can do this through the following commands:
```bash
sudo vi .hmy/blskeys/[yourBLSkey].pass
```
Once you're done press ESC, type `:x` and press ENTER.
{% endhint %}






