# Syncing with Rclone

{% hint style="warning" %}
This document introduces another centralized fast state syncing method using rclone. Please use it with caution. This guide is mainly used for a newly started node to catch up with the blockchain faster. Otherwise, the blockchain syncing may take weeks from genesis block.
{% endhint %}

Rclone db snapshot is sync'ed with blockchain frequently. However, there maybe a potential race condition when the rclone may fail due to our nodes were updating the db files at the same time. In this case, just re-run the rclone command to re-sync again.

## 1. Installing Rclone

For installing Rclone, please follow the instructions at [https://rclone.org](https://rclone.org/).

TL;DR, on a Linux system, you may run the following command.

```text
curl https://rclone.org/install.sh | sudo bash
```

## 2. Configuring Rclone

To check the location of the `rclone.conf`file run:

```bash
rclone config file
```

The `rclone.conf` file is usually located at `~/.config/rclone/rclone.conf` . 

Now run the following command to create the rclone.conf file.

```bash
cat<<-EOF > ~/.config/rclone/rclone.conf
[mainnet]
type = s3
provider = AWS
env_auth = false
region = us-west-1
acl = public-read
server_side_encryption = AES256
storage_class = REDUCED_REDUNDANCY
EOF
```

## 3. Running Rclone

Below is the command to sync the shard you want. Replace `<ShardID>`with the shard number you want to sync. Each of the rclone snapshot is around 1.7 Gb as of 05/14/2020. Shard 0 is around 1.8 Gb as of 5/14/2020. 

It may take up to 10 minutes to download depending on your network connection.

```bash
rclone -P sync mainnet:pub.harmony.one/mainnet.min/harmony_db_<ShardID> harmony_db_<ShardID>
```

{% hint style="info" %}
Nodes in shard 0 just need to sync `harmony_db_0`

Nodes in shard 1, 2, 3 need to sync both `harmony_db_0`, and `harmony_db_<ShardID>`
{% endhint %}

## 4. Cheat Sheet

#### shard0:

```bash
rclone -P sync mainnet:pub.harmony.one/mainnet.min/harmony_db_0 harmony_db_0
```

#### shard1:

```bash
rclone -P sync mainnet:pub.harmony.one/mainnet.min/harmony_db_0 harmony_db_0
rclone -P sync mainnet:pub.harmony.one/mainnet.min/harmony_db_1 harmony_db_1
```

#### shard2:

```bash
rclone -P sync mainnet:pub.harmony.one/mainnet.min/harmony_db_0 harmony_db_0
rclone -P sync mainnet:pub.harmony.one/mainnet.min/harmony_db_2 harmony_db_2
```

#### shard3:

```bash
rclone -P sync mainnet:pub.harmony.one/mainnet.min/harmony_db_0 harmony_db_0
rclone -P sync mainnet:pub.harmony.one/mainnet.min/harmony_db_3 harmony_db_3
```

After the sync, you may use `du -h harmony_db_*` command to check the size of the downloaded snapshots.

{% hint style="info" %}
`-P` will display a download progress & ETA.
{% endhint %}



