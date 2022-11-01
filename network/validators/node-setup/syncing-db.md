# 3. Syncing DB

## Validator Nodes

{% hint style="warning" %}
This document introduces another centralized fast state syncing method using rclone. Please use it with caution. This guide is mainly used for a newly started node to catch up with the blockchain faster. Otherwise, the blockchain syncing may take weeks from genesis block.
{% endhint %}

Rclone db snapshot is sync'ed with blockchain frequently. However, there maybe a potential race condition when the rclone may fail due to our nodes were updating the db files at the same time. In this case, just re-run the rclone command to re-sync again.

### 1. Installing Rclone

For installing Rclone, please follow the instructions at [https://rclone.org](https://rclone.org/).

TL;DR, on a Linux system, you may run the following command.

```
curl https://rclone.org/install.sh | sudo bash
```

{% hint style="info" %}
Make sure your rclone version is above **v1.53.2** . you can check version by `rclone version`
{% endhint %}

{% hint style="danger" %}
There is a daily snapshot of the rclone DB happening at 1:42:30 AM UTC for 3h. It is not advisable to perform a backup during those time.
{% endhint %}

### 2. Configuring Rclone

To check the location of the `rclone.conf`file run:

```bash
rclone config file
```

The `rclone.conf` file is usually located at `~/.config/rclone/rclone.conf` .

Now run the following command to create the rclone.conf file.

```bash
cat<<-EOF > ~/.config/rclone/rclone.conf
[release]
type = s3
provider = Storj
access_key_id = jwuyiin22hl6o5zxzlf76rc6csxa
secret_access_key = jyryzso3fv64zu4i2gmf33ed5hudb7qyatgpst22fnp57dfhviv4k
endpoint = gateway.us1.storjshare.io
EOF
```

{% hint style="info" %}
The above rclone config also work for the pangaea testnet network
{% endhint %}

### 3. Running Rclone

Below is the command to sync the shard you want. Replace `<ShardID>`with the shard number you want to sync. Shard 0 is around 300 Gb as of November 2021.

{% tabs %}
{% tab title="Mainnet" %}
```bash
rclone -P -L --checksum sync release:pub.harmony.one/mainnet.min/harmony_db_<ShardID> harmony_db_<ShardID> --multi-thread-streams 4 --transfers=32
```
{% endtab %}

{% tab title="Testnet" %}
```
rclone -P -L --checksum sync release:pub.harmony.one/testnet.min/harmony_db_<ShardID> harmony_db_<ShardID> --multi-thread-streams 4 --transfers=32
```
{% endtab %}
{% endtabs %}

If you encounter the following error:

```
NOTICE: Config file "/root/.config/rclone/rclone.conf" not found - using defaults
```

Add the option `--config=/home/harmony/.config/rclone/rclone.conf` to the command line.

{% hint style="info" %}
Nodes in shard 0 just need to sync `harmony_db_0`

Nodes in shard 1, 2, 3 need to sync both `harmony_db_0`, and `harmony_db_<ShardID>`
{% endhint %}

### 4. Cheat Sheet

#### shard0:

{% tabs %}
{% tab title="Mainnet" %}
```bash
rclone -P -L --checksum sync release:pub.harmony.one/mainnet.min/harmony_db_0 harmony_db_0 --multi-thread-streams 4 --transfers=32
```
{% endtab %}

{% tab title="Testnet" %}
```
rclone -P -L --checksum sync release:pub.harmony.one/testnet.min/harmony_db_0 harmony_db_0 --multi-thread-streams 4 --transfers=32
```
{% endtab %}
{% endtabs %}

#### Shard 1:

{% tabs %}
{% tab title="Mainnet" %}
```bash
rclone -P -L sync release:pub.harmony.one/mainnet.min/harmony_db_0 harmony_db_0 --multi-thread-streams 4 --transfers=8
rclone -P -L sync release:pub.harmony.one/mainnet.min/harmony_db_1 harmony_db_1 --multi-thread-streams 4 --transfers=8
```
{% endtab %}

{% tab title="Testnet" %}
```
rclone -P -L --checksum sync release:pub.harmony.one/testnet.min/harmony_db_0 harmony_db_0 --multi-thread-streams 4 --transfers=32
rclone -P -L --checksum sync release:pub.harmony.one/testnet.min/harmony_db_1 harmony_db_1 --multi-thread-streams 4 --transfers=32
```
{% endtab %}
{% endtabs %}

#### Shard 2:

{% tabs %}
{% tab title="Mainnet" %}
```bash
rclone -P -L sync release:pub.harmony.one/mainnet.min/harmony_db_0 harmony_db_0 --multi-thread-streams 4 --transfers=8
rclone -P -L sync release:pub.harmony.one/mainnet.min/harmony_db_2 harmony_db_2 --multi-thread-streams 4 --transfers=8
```
{% endtab %}

{% tab title="Testnet" %}
```
rclone -P -L --checksum sync release:pub.harmony.one/testnet.min/harmony_db_0 harmony_db_0 --multi-thread-streams 4 --transfers=32
rclone -P -L --checksum sync release:pub.harmony.one/testnet.min/harmony_db_2 harmony_db_2 --multi-thread-streams 4 --transfers=32
```
{% endtab %}
{% endtabs %}

#### Shard 3:

{% tabs %}
{% tab title="Mainnet" %}
```bash
rclone -P -L --checksum sync release:pub.harmony.one/mainnet.min/harmony_db_0 harmony_db_0 --multi-thread-streams 4 --transfers=32
rclone -P -L --checksum sync release:pub.harmony.one/mainnet.min/harmony_db_3 harmony_db_3 --multi-thread-streams 4 --transfers=32
```
{% endtab %}

{% tab title="Testnet" %}
```
rclone -P -L sync release:pub.harmony.one/testnet.min/harmony_db_0 harmony_db_0 --multi-thread-streams 4 --transfers=8
rclone -P -L sync release:pub.harmony.one/testnet.min/harmony_db_3 harmony_db_3 --multi-thread-streams 4 --transfers=8
```
{% endtab %}
{% endtabs %}

After the sync, you may use `du -h harmony_db_*` command to check the size of the downloaded snapshots.

{% hint style="info" %}
`-P` will display a download progress & ETA.
{% endhint %}

## Mainnet S0 Snapshot DB for validator

SnapDB is a new type of DB that doesn't contain any data before a given block (ie as of 4th March 2022, this is block 22816573), hence not suitable for RPC node

Mainnet validator in all shard 0/1/2/3 can use it with a size of 257G (as of 4th March 2022)

```
rclone -P -L --checksum sync release:pub.harmony.one/mainnet.snap/harmony_db_0 harmony_db_0 --multi-thread-streams 4 --transfers=32
```

## Non-Validating/Explorer Nodes

{% hint style="info" %}
As of 1st December 2022, the size for the shard 0 on mainnet is \~21TiB. Note that the bucket is currently not fully synced.
{% endhint %}

Please contact us at [devops@harmony.one](mailto:devops@harmony.one) if you need to access our archival db.

