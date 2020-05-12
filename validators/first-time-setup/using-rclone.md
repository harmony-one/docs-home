# Syncing with Rclone

This document introduces another centralized fast state syncing method using rclone. The document is still working-in-progress. Please use it with caution. This guide is mainly used for a newly started node to catch up with the blockchain faster. Otherwise, the blockchain syncing may take weeks.

Rclone db snapshot is sync'ed with blockchain once a day. It is more recent than the db tarball. However, there maybe a potential race condition when the rclone may fail due to our nodes were updating the db files at the same time. In this case, just re-run the rclone command to re-sync again.

## 1. Installing Rclone

If you don't know what is rclone, please visit the rclone website for some more info and usage.

Install rclone =&gt; [https://rclone.org/](https://rclone.org/)

## 2. Configuring Rclone

Add the following `rclone.conf` file to `~/.config/rclone` directory

```text
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

Below is the command to sync the shard you want. Replace `<ShardID>`with the shard number you want to sync.

```bash
rclone sync mainnet:pub.harmony.one/mainnet.min/harmony_db_<ShardID> harmony_db_<ShardID>
```



