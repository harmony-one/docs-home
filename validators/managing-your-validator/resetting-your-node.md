# Resetting Your Node

If the Open Staking Testnet network is reset, you will need to reset the database files \(`harmony_db`\), networking files \(`.dht*`\), delete the existing `harmony` binary, and `md5sum.txt` to download the new binary.

{% hint style="danger" %}
Be very careful running `sudo rm -rf` . It could delete your computer. Copy the below commands as is.
{% endhint %}

```text
sudo rm -rf harmony_db_*
sudo rm -rf .dht*
sudo rm -rf harmony
sudo rm -rf md5sum.txt
```

Then run your node again in your `tmux` session.

```text
./node.sh -S -N staking -z -k [BLS KEY FILE].key
```

And then [create your validator](resetting-your-node.md) again.

