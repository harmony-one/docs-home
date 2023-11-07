# 3. Syncing DB

## Simple algorithm to distinguish between snapshot types

Using answers for these questions you can easily understand which snapshot type you will need

<figure><img src="../../../.gitbook/assets/DB_types_harmony.png" alt=""><figcaption></figcaption></figure>

## Validator Nodes

{% hint style="warning" %}
This document introduces another centralized fast state syncing method using rclone. Please use it with caution. This guide is mainly used for a newly started node to catch up with the blockchain faster. Otherwise, the blockchain syncing may take weeks from genesis block.
{% endhint %}

{% hint style="info" %}
Rclone db snapshot is synced with blockchain frequently. However, there maybe a potential race condition when the rclone may fail due to our nodes were updating the db files at the same time. In this case, just re-run the rclone command to re-sync again.
{% endhint %}

### 1. Installing Rclone

For installing Rclone, please follow the instructions at [https://rclone.org](https://rclone.org/).

**TL;DR:** on a Linux system, you may run the following command:

```bash
curl https://rclone.org/install.sh | sudo bash
```

{% hint style="info" %}
Make sure your rclone version is above **v1.53.2** . you can check version by `rclone version`
{% endhint %}

### 2. Configuring Rclone

To check the location of the `rclone.conf`file run:

```bash
rclone config file
```

The `rclone.conf` file is usually located at `~/.config/rclone/rclone.conf` .

Now run the following command to create the rclone.conf file:

```bash
cat<<-EOF > ~/.config/rclone/rclone.conf
[snap]
type = webdav
vendor = other
user = snap
pass = ufbTDtK0fENuutwuDOHae57xT8URsZVIcdotK30T5A
EOF
```

### 2.1 BEWARE: Understanding the \`rclone sync\`

{% hint style="danger" %}
The most important parts in bold:

Sync the source to the destination, **changing the destination only**. Doesn't transfer files that are identical on source and destination, testing by size and modification time or MD5SUM. **Destination is updated to match source, including deleting files if necessary** (except duplicate objects). [Link to the full rclone documentation](https://rclone.org/commands/rclone\_sync/).

`sync` command was chosen because you need to have your blockchain data folder to be identical with the snapshot data
{% endhint %}

**As user you need to carefully get the full path to the folder and as destination. If you have some important data in the destination, please move it somewhere else.**&#x20;

{% hint style="info" %}
Usually data dir folder is \``` ./` `` which means folder in which harmony is running

You can double check this via:

`ls -l | grep 'harmony_db_'`

`Expected result id is name with shard number on the end, e.x. harmony_db_0.`
{% endhint %}

Q: How to get the full path to the your blockchain data folder if it isn't **default**?

1. Check how do you start harmony via `ps -ef | grep harmony`  and check for the `--datadir` option, if you don't have it go to the following step, else to the 3rd
2. Check the harmony.conf for DataDir option or check your `grep DataDir harmony.conf`
3. Go to the folder from the cmd option if have it or to folder from config if you don't have cmd option, do the following:

```bash
cd your_data_dir # folder from the cmd line or config
ls -l # it will give the shard folder name like harmony_db_0/
pwd # now you have full path to your data dir
```

### 3. Shard 0 validator - Snap DB sync

{% hint style="info" %}
SnapDB is a type of DB that contain a snapshot of the state at a given block. It doesn't have any **block history** and **hence not suitable for RPC node.**
{% endhint %}

Below is the command to sync the Snap DB for the shard 0. It is around 100 Gb as of October 2023:

{% hint style="danger" %}
**Important**: Since this can cause data loss, test first with the `--dry-run` or the `--interactive`/`-i` flag.
{% endhint %}

<pre class="language-bash"><code class="lang-bash">YOUR_DATA_DIR='./' # This is the default installation, change it you use something else
<strong>rclone -P -L --webdav-url 'http://snapdb.s0.t.hmny.io/webdav'  --checksum sync \
</strong>  snap: "${YOUR_DATA_DIR}harmony_db_0" --multi-thread-streams 4 --transfers=32 --verbose
</code></pre>

Small explanation for flags used to save your time with rclone manual: &#x20;

```bash
# --webdav-url - source of the data and URL of http host to connect to
# YOUR_DATA_DIR/harmony_db_0 - your destination
# -P - flag to show the progress
# -L - Follow symlinks and copy the pointed to item
# --checksum - Normally rclone will look at modification time and size of 
#  files to see if they are equal.  If you set this flag then rclone will 
#  check the file hash and size to determine if files are equal
# snap: - the way how do you tell which config is used 
# --multi-thread-streams 4 - When using multi thread downloads this 
#  sets the maximum number of streams to use
# --transfers=32 - The number of file transfers to run in parallel.
#   It can sometimes be useful to set this to a smaller number if the remote is giving a lot of timeouts or bigger if you have lots of bandwidth and a fast remote.
# --verbose - With -v rclone will tell you about each file that is transferred and a small number of significant events.
# sync - make the origin and destination the same, after 1st run add the deltas
```

### 4. Full db sync for appropriate shard &#x20;

{% hint style="info" %}
Since v4.3.12 shard 1 doesn't need to download anymore shard 0 DB. Instead, the node will download automatically the blocks required for the node in shard 1 to work.
{% endhint %}

Each node will simply need to rclone its own DB.

### 4.1 Shard0 RPC Explorer node (non archival)

{% hint style="danger" %}
**Important**: Since this can cause data loss, test first with the `--dry-run` or the `--interactive`/`-i` flag.
{% endhint %}

<pre class="language-bash"><code class="lang-bash">YOUR_DATA_DIR='./' # This is the default installation, change it you use something else
<strong>rclone -P -L --webdav-url 'http://fulldb.s0.t.hmny.io/webdav' \
</strong>   --checksum sync snap: "${YOUR_DATA_DIR}harmony_db_0" --multi-thread-streams 4 --transfers=32 --verbose 
</code></pre>

### 4.2 Shard 1 validator

{% hint style="danger" %}
**Important**: Since this can cause data loss, test first with the `--dry-run` or the `--interactive`/`-i` flag.
{% endhint %}

```bash
YOUR_DATA_DIR='./' # This is the default installation, change it you use something else
rclone -P -L --webdav-url 'http://fulldb.s1.t.hmny.io/webdav' \
   --checksum sync snap: "${YOUR_DATA_DIR}harmony_db_1" --multi-thread-streams 4 --transfers=32 --verbose 
```

## Archival snapshot for the Non-Validating/Explorer Nodes

{% hint style="info" %}
As of 1st October 2023, the size for the shard 0 on mainnet is \~23TiB. Note that the bucket is currently not fully synced.
{% endhint %}

{% hint style="warning" %}
Please contact us at [devops@harmony.one](mailto:devops@harmony.one) if you need to access our archival db.
{% endhint %}

