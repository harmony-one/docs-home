---
description: Using node.sh
---

# Running a Node

{% hint style="warning" %}
As per instructions on the [cloud guides](../../../cloud-setup/cloud-guides/), the host needs to open up port **9000** for blockchain consensus messages and port **6000** for blockchain state syncing. Other ports are NOT necessary for syncing and should NOT be opened to the internet if you are staking only.
{% endhint %}

* 9000 port is used for blockchain consensus messages \(**base port**\)
* 6000 port is used for blockchain state syncing \(base port - 3000\)
* 9500 port is used for SDK RPC service \(base port + 500\)
* 9800 port is used for Websocket service \(base port + 800\)

The 9500, 9800 ports are only listened by localhost 127.0.0.1 by default. If it is required for the host to accept external links, the `-P` command line option can be specified in `node.sh` to listen to a public IP. Be careful opening these two ports to the internet!

## Downloading node.sh

Run the following command to download the node.sh script:

```bash
curl -LO https://harmony.one/node.sh && chmod a+x node.sh
```

## Configuring the BLS keys

**1.** You need to manually create a folder called `.hmy/blskeys`:

```bash
mkdir -p .hmy/blskeys
```

**2.** Copy all the [previously created BLS key\(s\)](https://docs.harmony.one/home/validators/first-time-setup/generating-a-bls-key) to this new folder:

```bash
cp *.key .hmy/blskeys
```

{% hint style="warning" %}
Make sure all your BLS keys belong to the same shard when using multiple BLS keys. You can use the command below to check each one of them.
{% endhint %}

```bash
./hmy --node="https://api.s0.t.hmny.io" utility shard-for-bls [BLS PUBLIC KEY]
```

**3.** For each BLS key file, a corresponding `<blskey>.pass` file needs to be created inside folder`.hmy/blskeys`with the passphrase inside it.

{% hint style="warning" %}
For any `.key` if no passphrase file is available, it will use the default specified when running the node e.g., `./node.sh -p blspass.txt`
{% endhint %}

## Running Using Systemd

{% hint style="info" %}
Execute all the following commands  using the `root` user. On this example, we will be installing the harmony daemon for user `harmony-user` on its home directory. Daemon will be configured with the `root` user but it will run with `harmony-user`at the end.
{% endhint %}

Create the `harmony.service` file:

{% tabs %}
{% tab title="Ubuntu LTS" %}
```bash
vi /etc/systemd/system/harmony.service
```
{% endtab %}
{% endtabs %}

Add the content below to the file and save it. Change `User` to the local user you will be running the daemon and also `WorkingDirectory` to the home directory where you downloaded `node.sh` previously. Parameter `ExecStart` needs to point to this same directory.

{% tabs %}
{% tab title="Ubuntu LTS" %}
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
ExecStart=/home/harmony-user/node.sh -S -z
SyslogIdentifier=harmony
StandardOutput=file:/var/log/hmy.log
StandardError=file:/var/log/hmy_error.log
StartLimitInterval=0
LimitNOFILE=65536
LimitNPROC=65536

[Install]
WantedBy=multi-user.target
```
{% endtab %}
{% endtabs %}

Give the necessary permissions to run the daemon service, enable it and start it:

```bash
chmod 755 /etc/systemd/system/harmony.service
systemctl enable harmony.service
service harmony start
```

If you want to check if the daemon is running correctly you can use:

```bash
service harmony status
```

To stop the service use:

```bash
service harmony stop
```

## Checking if the Node is Syncing

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

## Non-validating Nodes

{% hint style="info" %}
Non-validating nodes will not sign blocks on blockchain, thus they cannot be used for staking. They can be used though by exchanges or wallet providers to broadcast transactions, query balances, fetch transaction data using RPC interfaces, etc.
{% endhint %}

Use parameter `-T` to define the node type and `-i` to define the shard you want your non-validating node to work. On the example below we will be running our non-validating node on shard 0:

```text
./node.sh -S -T explorer -i 0
```

