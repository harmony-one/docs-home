---
description: This page is under construction.
---

# Under Construction

{% hint style="danger" %}
Don't use this now, we are updating the docs and will make official when ready.
{% endhint %}

{% hint style="warning" %}
As per instructions on the [cloud guides](../../../cloud-setup/cloud-guides/), the host needs to open up port **9000** for blockchain consensus messages and port **6000** for blockchain state syncing. Other ports are NOT necessary for syncing and should NOT be opened to the internet if you are staking only.
{% endhint %}

* 9000 port is used for blockchain consensus messages \(**base port**\)
* 6000 port is used for blockchain state syncing \(base port - 3000\)
* 9500 port is used for SDK RPC service \(base port + 500\)
* 9800 port is used for Websocket service \(base port + 800\)

## 1. Downloading Files

Download the latest `node.sh` file:

```bash
curl -LO https://harmony.one/node.sh && chmod a+x node.sh
```

Download the binary files into the `staging` folder:

```bash
./node.sh -d
```

Move files from `staging` folder to current folder:

```bash
mv staging/* ./
```

## 2. Configuring the BLS Keys

You need to manually create a folder called `.hmy/blskeys`:

```bash
mkdir -p .hmy/blskeys
```

Copy all the [previously created BLS key\(s\)](https://docs.harmony.one/home/validators/first-time-setup/generating-a-bls-key) to this new folder:

```bash
cp *.key .hmy/blskeys
```

{% hint style="warning" %}
Make sure all your BLS keys belong to the same shard when using multiple BLS keys. You can use the command below to check each one of them.
{% endhint %}

```bash
./hmy --node="https://api.s0.t.hmny.io" utility shard-for-bls [BLS PUBLIC KEY]
```

For each BLS key file, a corresponding `<blskey>.pass` file needs to be created inside folder`.hmy/blskeys`with the passphrase inside it.

## 3. Configuring the Node Binary

Harmony Node binary can be started with:

1. CLI flags parsing
2. A config file
3. CLI flag and config file combined

The esiest way is setting up via config file. A `harmony.conf` file will be created and the default node options will be set in the file in TOML formatting:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./harmony dumpconfig --network mainnet harmony.conf
```
{% endtab %}

{% tab title="Testnet" %}
```
./harmony dumpconfig --network testnet harmony.conf
```
{% endtab %}
{% endtabs %}

The content of the config file can be modified for custom node start up. By default, ports 9500 and 9800 listend to localhost \(127.0.0.1\) only.

If you want, you can start the Node Binary with **CLI flags parsing only** or **CLI flag and config file combined**. For a full list of active flags as well as examples run the Node Binary with  the`--help` option:

```bash
./harmony --help
```

## 4. Running Using Systemd

{% hint style="info" %}
On this example, we will be installing the harmony daemon for user `harmony-user` on its home directory. Daemon will be configured with the `sudo` user but it will run with `harmony-user`at the end.
{% endhint %}

Create the `harmony.service` file:

```bash
sudo vi /etc/systemd/system/harmony.service
```

Add the content below to the file and save it. Change `User` to the local user you will be running the daemon and also `WorkingDirectory` to the home directory where you downloaded `node.sh` previously. Parameter `ExecStart` needs to point to this same directory.

```bash
[Unit]
Description=Harmony daemon
After=network-online.target

[Service]
Type=simple
Restart=always
RestartSec=1
User=harmony-user
WorkingDirectory=/home/harmony-user
ExecStart=/home/harmony-user/harmony -c harmony.conf
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

You can **stop**, **start**, **restart** or get the **status** of the harmony service running the commands below:

{% tabs %}
{% tab title="Stop" %}
```bash
sudo service harmony stop
```
{% endtab %}

{% tab title="Start" %}
```
sudo service harmony start
```
{% endtab %}

{% tab title="Restart" %}
```
sudo service harmony restart
```
{% endtab %}

{% tab title="Status" %}
```
sudo service harmony status
```
{% endtab %}
{% endtabs %}

## 5. Checking if the Node is Syncing

**1.** To check if your node is syncing properly, run the below command and check that the block height is greater than 0.

```bash
./hmy blockchain latest-headers
```

{% hint style="success" %}
Harmony relies on a beacon shard chain \(aka shard 0\) to facilitate cross shard transaction. For the node to be fully working both your non shard 0 and shard 0 needs to be fully synced.
{% endhint %}

**2.** Confirm that you are fully synced before continuing. Issue  the command in the format **./hmy --node= "\[SHARD\_RPC\_ENDPOINT\]" blockchain latest-headers**,  where  
SHARD\_RCP\_ENDPOINT would be having that format : api.s\[Shard \#\].\[NETWORK\].hmny.io   
ex :

```bash
./hmy --node="https://api.s0.t.hmny.io" blockchain latest-headers
```

{% hint style="success" %}
For a complete reference of all available enpoints on both mainnet and testnet, please click [here](https://monitor.hmny.io/status). For examples, we will be using the shard 0 mainnet endpoint.
{% endhint %}

**3.** Verify the blocks shown on steps 1 and 2 are closed or equals to each other.

