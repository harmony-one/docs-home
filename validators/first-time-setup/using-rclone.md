# Syncing with Rclone

{% hint style="warning" %}
This document introduces another centralized fast state syncing method using rclone. Please use it with caution. This guide is mainly used for a newly started node to catch up with the blockchain faster. Otherwise, the blockchain syncing may take weeks from genesis block.
{% endhint %}

Rclone db snapshot is sync'ed with blockchain frequently. However, there maybe a potential race condition when the rclone may fail due to our nodes were updating the db files at the same time. In this case, just re-run the rclone command to re-sync again.

## 1. Installing Rclone

For installing Rclone, please follow the instructions at [https://rclone.org](https://rclone.org/).

## 2. Configuring Rclone

To check the location of the `rclone.conf`file run:

```bash
rclone config file
```

The `rclone.conf` file is usually located at `~/.config/rclone/rclone.conf` . Now edit the file and add the information below:

```bash
[mainnet]
type = s3
provider = AWS
env_auth = false
region = us-west-1
acl = public-read
server_side_encryption = AES256
storage_class = REDUCED_REDUNDANCY
```

## 3. Running Rclone

Below is the command to sync the shard you want. Replace `<ShardID>`with the shard number you want to sync. Each of the rclone snapshot is around ~1.7 Gb as of 05/14/2020. It may take up to 10 minutes for the full sync depending on your network condition.

```bash
rclone sync mainnet:pub.harmony.one/mainnet.min/harmony_db_<ShardID> harmony_db_<ShardID>
```

{% hint style="info" %}
Nodes in shard 0 just need to sync `harmony_db_0`

Nodes in shard 1, 2, 3 need to sync both `harmony_db_0`, and `harmony_db_<ShardID>`
{% endhint %}

After the sync, you may use a simple `du -h harmony_db_*` command to check the size of the downloaded snapshots.

