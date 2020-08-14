# Using Node.sh

{% hint style="warning" %}
This option will be **deprecated** and is **not recommended** anymore. Please setup your node [Using Binary CLI](using-binary-cli.md) or [Using AutoNode](using-autonode/).
{% endhint %}

## 1. Download Node.sh

```bash
curl -LO https://harmony.one/node.sh && chmod a+x node.sh
./node.sh -d && mv staging/* ./
```

### 1.2. Setup Node.sh

You can run your the node using flags parsing:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./node.sh -S -z
```
{% endtab %}

{% tab title="Testnet" %}
```
node.sh -S -z -N testnet
```
{% endtab %}
{% endtabs %}

A full list of active flags as well as examples can be access through running `node.sh` with `--help` option:

```bash
./node.sh --help
```

Output:

```text
Usage: node.sh [options]

Options:
   -c             back up database/logs and start clean (not for mainnet)
                  (use only when directed by Harmony)
   -C             disable interactive console for bls passphrase (default: enabled)
   -1             do not loop; run once and exit
   -h             print this help and exit
   -k KEYFILE     use the given BLS key files
   -s             run setup env only (must run as root)
   -S             run the node.sh as non-root user (default: run as root)
   -p passfile    use the given BLS passphrase file
   -d             just download the Harmony binaries (default: off)
   -D             do not download Harmony binaries (default: download when start)
   -N network     join the given network (mainnet, testnet, staking, partner, stress, devnet, tnet; default: mainnet)
   -n port        specify the public base port of the node (default: 9000)
   -T nodetype    specify the node type (validator, explorer; default: validator)
   -i shardid     specify the shard id (valid only with explorer node; default: 1)
   -a dbfile      specify the db file to download (default:off)
   -U FOLDER      specify the upgrade folder to download binaries
   -P             enable public rpc end point (default:off)
   -v             print out the version of the node.sh
   -V             print out the version of the Harmony binary
   -z             run in staking mode
   -y             run in legacy, foundational-node mode (default)
   -Y             verify the signature of the downloaded binaries (default: off)
   -m minpeer     specify minpeers for bootstrap (default: 6)
   -f blsfolder   folder that stores the bls keys and corresponding passphrases (default: ./.hmy/blskeys)
   -A             enable archival node mode (default: off)
   -B blacklist   specify file containing blacklisted accounts as a newline delimited file (default: ./.hmy/blacklist.txt)
   -r address     start a pprof profiling server listening on the specified address
   -I             use statically linked Harmony binary (default: true)
   -R tracefile   enable p2p trace using tracefile (default: off)
   -l             limit broadcasting of invalid transactions (default: off)
   -L log_level   logging verbosity: 0=silent, 1=error, 2=warn, 3=info, 4=debug, 5=detail (default: 3)
   
Examples:

# start node program with all key/passphrase under .hmy/blskeys
# first try to unlock account with .pass file. If pass file not exist or cannot decrypt, prompt to get passphrase.
   node.sh -S 

# start node program w/o accounts
   node.sh -S -k mybls1.key,mybls2.key

# download beacon chain (shard0) db snapshot
   node.sh -i 0 -b

# just re-download the harmony binaries
   node.sh -d

# start a non-validating node in shard 1
# you need to have a dummy BLSKEY/pass file using 'touch BLSKEY; touch blspass'
   node.sh -S -k BLSKEY -p blspass -T explorer -i 1

# upgrade harmony binaries from specified repo
   node.sh -1 -U upgrade

# start the node in a different port 9010
   node.sh -n 9010

# multi-bls: specify folder that contains bls keys
   node.sh -S -f /home/xyz/myfolder

# multi-bls using default passphrase: place all keys under .hmy/blskeys
# supply passphrase file using -p option (single passphrase will be used for all bls keys)
   node.sh -S -p blspass.txt

# disable interactive console for passphrase (prepare .pass file before running command)
   node.sh -S -C
```

## 2. Setup Systemd

{% hint style="info" %}
On this example, we will be installing the harmony daemon for user `harmony` on its home directory. Daemon will be configured with `sudo`but it will run with the `harmony`user at the end.
{% endhint %}

Create the `harmony.service` file:

```bash
sudo vi /etc/systemd/system/harmony.service
```

Add the content below to the file and save it. Change `User` to the local user you will be running the daemon and also `WorkingDirectory` to the home directory where you downloaded the harmony binary file previously. Parameter `ExecStart` needs to point to this same directory. On the example below we will be running node.sh using the `harmony.conf` file.

```bash
[Unit]
Description=Harmony daemon
After=network-online.target

[Service]
Type=simple
Restart=always
RestartSec=1
User=harmony
WorkingDirectory=/home/harmony
ExecStart=/home/harmony/node.sh -S -z
SyslogIdentifier=harmony
StartLimitInterval=0
LimitNOFILE=65536
LimitNPROC=65536

[Install]
WantedBy=multi-user.target
```

Give the necessary permissions to run the daemon service, enable it and start it:

```bash
sudo chmod 755 /etc/systemd/system/harmony.service
sudo systemctl enable harmony.service
sudo service harmony start
```

If you want to check the status of the daemon you can use:

```bash
sudo service harmony status
```

To restart, or stop the service daemon you can run:

{% tabs %}
{% tab title="Restart" %}
```bash
sudo service harmony restart
```
{% endtab %}

{% tab title="Stop" %}
```
sudo service harmony stop
```
{% endtab %}
{% endtabs %}

