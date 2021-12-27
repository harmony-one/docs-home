# Checking A Node

## 1. Check Node Running Version

To check the node version that is running, run the command below:

```bash
./hmy utility metadata
```

## **2. Check if Node is Syncing**

**1.** To check if your node is syncing properly, run the command below and check that the block height of the shard(s).

```bash
./hmy blockchain latest-headers
```

{% hint style="success" %}
Harmony relies on a beacon shard chain (aka shard 0) to facilitate cross shard transaction. For the node to be fully working both your non shard 0 and shard 0 needs to be fully synced.
{% endhint %}

**2.** Before continuing, check if your node is fully synced using an external endpoint. Replace parameter `--node` with the enpoint you want to compare with. Check the examples below  for shard 0 on mainnet and testnet. Just change the edpoints to do the comparison with other shards.

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" blockchain latest-headers
```
{% endtab %}

{% tab title="Testnet" %}
```bash
./hmy --node="https://api.s0.b.hmny.io" blockchain latest-headers
```
{% endtab %}
{% endtabs %}

{% hint style="success" %}
For a complete reference of all available enpoints on both mainnet and testnet, please click [here](https://monitor.hmny.io/status). Alternatively you can use the [Block Explorers](broken-reference) for a visual comparison.
{% endhint %}

**3.** Verify if blocks shown on steps 1 and 2 are closer or equal to each other. If so, your node should have caught up!
