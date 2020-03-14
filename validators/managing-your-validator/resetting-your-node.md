# Resetting Your Node

If the Open Staking Testnet network is reset, you will need to reset the database files \(`harmony_db`\), networking files \(`.dht*`\), delete the existing `harmony` binary, and `md5sum.txt` to download the new binary. Use the `-c` option on node.sh to clear away the old data.

Then run your node again in your `tmux` session.

```text
./node.sh -S -c -I -N staking -z -k [BLS KEY FILE].key
```

Or if you are running with Multiple BLSkeys, run your node with the following command

```text
./node.sh -S -c -I -N staking -z -M
```

And then [create your validator](../first-time-setup/creating-a-validator.md) again.

