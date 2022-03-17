# Using Node Binary

{% hint style="info" %}
As per instructions on the [cloud guides](../../../server-setup/cloud-guides/), the host needs to open up port **9000** for blockchain consensus messages and port **6000** for blockchain state syncing. Other ports are NOT necessary for syncing and should NOT be opened to the internet if you are staking only.
{% endhint %}

* 9000 port is used for blockchain consensus messages (**base port**)
* 6000 port is used for blockchain state syncing (base port - 3000)
* 9500 port is used for SDK RPC service (base port + 500)
* 9800 port is used for Websocket service (base port + 800)

The 9500, 9800 ports are only listened by localhost 127.0.0.1 by default.

## 1. Download Node Binary

Before we proceed to next steps we need to download the node binary first:

{% tabs %}
{% tab title="x86_64 (Mainnet)" %}
```bash
curl -LO https://harmony.one/binary && mv binary harmony && chmod +x harmony
```
{% endtab %}

{% tab title="x86_64 (Testnet) " %}
```bash
curl -LO https://harmony.one/binary_testnet && mv binary_testnet harmony && chmod +x harmony
```
{% endtab %}

{% tab title="arm64 (Mainnet)" %}
```bash
curl -LO https://harmony.one/binary-arm64 && mv binary-arm64 harmony && chmod +x harmony
```
{% endtab %}
{% endtabs %}

Check the node binary version that was downloaded:

```
./harmony -V
```

The below explain the different method the node binary can be used. Option 1 is what being used when setting up systemd ([at step 2](https://docs.harmony.one/home/validators/node-setup/installing-updating/installing-node/using-binary-cli#option-2-setup-using-cli-flags-parsing)).

{% hint style="danger" %}
If you choose another method make sure to use the correct command line
{% endhint %}

### Option 1: Setup Using Config File (recommended)

All the start options can be persisted and loaded from a single config file. To start a node, the following steps are also available\*\*:\*\*

1. Dump the default config.
2. Customize the config file.
3. Run harmony node with the config file.

#### Dump the Default Config File

{% tabs %}
{% tab title="Mainnet" %}
```bash
./harmony config dump harmony.conf
```
{% endtab %}

{% tab title="Testnet" %}
```
./harmony config dump --network testnet harmony.conf
```
{% endtab %}
{% endtabs %}

A file `harmony.conf` is created and the default node options are set in the file in TOML formatting. Here is an example:

```
Version = "2.1.0"

[BLSKeys]
  KMSConfigFile = ""
  KMSConfigSrcType = "shared"
  KMSEnabled = false
  KeyDir = "./.hmy/blskeys"
  KeyFiles = []
  MaxKeys = 10
  PassEnabled = true
  PassFile = ""
  PassSrcType = "auto"
  SavePassphrase = false

[DNSSync]
  Client = true
  LegacySyncing = false
  Port = 6000
  Server = true
  ServerPort = 6000
  Zone = "t.hmny.io"

[General]
  DataDir = "./"
  IsArchival = false
  IsBeaconArchival = false
  IsOffline = false
  NoStaking = false
  NodeType = "validator"
  ShardID = -1

[HTTP]
  Enabled = true
  IP = "127.0.0.1"
  Port = 9500
  RosettaEnabled = false
  RosettaPort = 9700

[Log]
  FileName = "harmony.log"
  Folder = "./latest"
  RotateSize = 100
  Verbosity = 3

  [Log.VerbosePrints]
    Config = false

[Network]
  BootNodes = ["/dnsaddr/bootstrap.t.hmny.io"]
  NetworkType = "mainnet"

[P2P]
  IP = "0.0.0.0"
  KeyFile = "./.hmykey"
  Port = 9000

[Pprof]
  Enabled = false
  ListenAddr = "127.0.0.1:6060"

[RPCOpt]
  DebugEnabled = false
  RateLimterEnabled = true
  RequestsPerSecond = 1000

[Sync]
  Concurrency = 6
  DiscBatch = 8
  DiscHardLowCap = 6
  DiscHighCap = 128
  DiscSoftLowCap = 8
  Downloader = false
  Enabled = false
  InitStreams = 8
  MinPeers = 6

[TxPool]
  BlacklistFile = "./.hmy/blacklist.txt"

[WS]
  Enabled = true
  IP = "127.0.0.1"
  Port = 9800
```

The content of the config file can be modified for custom node start up command.

For example, to open the public HTTP RPCs, change the field `IP` under `[HTTP]` tag to `"0.0.0.0"`:

```
[HTTP]
  Enabled = true
  IP = "0.0.0.0"
  Port = 9500
  RosettaEnabled = false
  RosettaPort = 9700
```

To run harmony internal nodes under legacy mode instead of staking mode, change the field `NoStaking` under `[General]` tag to `true`:

```
[General]
  DataDir = "./"
  IsArchival = false
  IsBeaconArchival = false
  IsOffline = false
  NoStaking = true
  NodeType = "validator"
  ShardID = -1
```

To enable streamsync, modify the below two sections (Experimental)

{% tabs %}
{% tab title="Testnet" %}
```bash
[DNSSync]
  Client = false
  LegacySyncing = false
  Port = 6000
  Server = true
  ServerPort = 6000
  Zone = "b.hmny.io"
  
[Sync]
  Concurrency = 4
  DiscBatch = 8
  DiscHardLowCap = 4
  DiscHighCap = 1024
  DiscSoftLowCap = 4
  Downloader = true
  InitStreams = 4
  MinPeers = 4
```
{% endtab %}
{% endtabs %}

{% hint style="success" %}
Stream Sync is the new harmony Syncing method allowing to get rid of the previous sync via DNS causing issue when the DNS node wasn't in sync.
{% endhint %}

#### Start the node with Config File

Harmony node binary is able to start with options provided by the config file:

```
./harmony -c harmony.conf
```

The values stored in the config file will be read and parsed to harmony as node start options.

### Option 2: Setup Using Flag Parsing

You can run your node binary using flag parsing:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./harmony
```
{% endtab %}

{% tab title="Testnet" %}
```
./harmony --network testnet
```
{% endtab %}
{% endtabs %}

A full list of active flags as well as examples can be accessed through running the binary with `--help` option:

```
./harmony --help
```

Output:

```
Examples usage:

# start a validator node with default bls folder (default bls key files in ./.hmy/blskeys)
    ./harmony

# start a validator node with customized bls key folder
    ./harmony --bls.dir [bls_folder]

# start a validator node with open RPC endpoints and customized ports
    ./harmony --http.ip=0.0.0.0 --http.port=[http_port] --ws.ip=0.0.0.0 --ws.port=[ws_port]

# start an explorer node
    ./harmony --run=explorer --run.archive --run.shard=[shard_id]

# start a harmony internal node on testnet
    ./harmony --run.legacy --network
    
Usage:
  harmony [flags]
  harmony [command]

Available Commands:
  dumpconfig  dump the config file for harmony binary configurations
  help        Help about any command
  version     print version of the harmony binary

Flags:
      --bls.dir string            directory for BLS keys (default "./.hmy/blskeys")
      --bls.keys strings          a list of BLS key files (separated by ,)
      --bls.kms                   enable BLS key decryption with AWS KMS service (default true)
      --bls.kms.config string     json config file for KMS service (region and credentials)
      --bls.kms.src string        the AWS config source (region and credentials) for KMS service (shared, prompt, file) (default "shared")
      --bls.pass                  enable BLS key decryption with passphrase (default true)
      --bls.pass.file string      the pass file used for BLS decryption. If specified, this pass file will be used for all BLS keys
      --bls.pass.save             after input the BLS passphrase from console, whether to persist the input passphrases in .pass file
      --bls.pass.src string       source for BLS passphrase (auto, file, prompt) (default "auto")
      --bootnodes strings         a list of bootnode multiaddress (delimited by ,)
  -c, --config string             load node config from the config toml file.
      --datadir string            directory of chain database (default "./")
      --dns.port int              port of customized dns node (default 9000)
      --dns.zone string           use customized peers from the zone for state syncing
  -h, --help                      help for harmony
      --http                      enable HTTP / RPC requests (default true)
      --http.ip string            ip address to listen for RPC calls. Use 0.0.0.0 for public endpoint (default "127.0.0.1")
      --http.port int             rpc port to listen for HTTP requests (default 9500)
      --log.dir string            directory path to put rotation logs (default "./latest")
      --log.max-size int          rotation log size in megabytes (default 100)
      --log.name string           log file name (e.g. harmony.log) (default "harmony.log")
  -v, --log.verb int              logging verbosity: 0=silent, 1=error, 2=warn, 3=info, 4=debug, 5=detail (default 3)
  -n, --network string            network to join (mainnet, testnet, pangaea, localnet, partner, stressnet, devnet) (default "mainnet")
      --p2p.keyfile string        the p2p key file of the harmony node (default "./.hmykey")
      --p2p.port int              port to listen for p2p protocols (default 9000)
      --pprof                     enable pprof profiling
      --pprof.addr string         listen address for pprof (default "127.0.0.1:6060")
      --run string                run node type (validator, explorer) (default "validator")
      --run.archive               run node in archive mode
      --run.legacy                whether to run node in legacy mode
      --run.shard int             run node on the given shard ID (-1 automatically configured by BLS keys) (default -1)
      --txpool.blacklist string   file of blacklisted wallet addresses (default "./.hmy/blacklist.txt")
  -V, --version                   display version info
      --ws                        enable websocket endpoint (default true)
      --ws.ip string              ip endpoint for websocket. Use 0.0.0.0 for public endpoint (default "127.0.0.1")
      --ws.port int               port for websocket endpoint (default 9800)

Use "harmony [command] --help" for more information about a command.
```

### Option 3: Setup Using Flag Parsing and a Config file combined

{% hint style="info" %}
If both config file and flag is provided, the node option stored in config file will be override by the values given in flag.
{% endhint %}

For example, In config file `harmony.conf`, HTTP server is enabled, and is open to public:

```
[HTTP]
  Enabled = true
  IP = "0.0.0.0"
  Port = 9500
  RosettaEnabled = false
  RosettaPort = 9700
```

And a flag is also provided during the node start command to disable the HTTP server:

```
./harmony -c harmony.conf --http=false
```

In this case, the command line flags will override the settings in the config file and thus the HTTP server is disabled.

```
> curl localhost:9500
curl: (7) Failed to connect to localhost port 9500: Connection refused
```

{% hint style="warning" %}
The above steps would have you started the node, please CTRL+C, so you can continue with step 2.
{% endhint %}

### Non-Validating/Explorer Nodes

A Non-validating Node is a node that runs in archival mode and does not join the consensus.

{% hint style="warning" %}
Check [here](../../../server-setup/requirements.md#explorer-node-recommendation) for Explorer Node requirements.
{% endhint %}

Check [here](../../syncing-db.md#archival-node) for instructions on how to sync your node in archival mode.

{% hint style="info" %}
Keep in mind that the storage space used increases around \~50+ GB per month on s0 due to staking transaction being stored. Other shard should take around 25GB per month. Please plan your storage space accordingly.
{% endhint %}

The following steps assume the node is connected to mainnet on shard 0, which is required for all exchanges.

If you are using the config file, which is the recommended way to configure your node, change the settings to the ones below:

```
 [General]
  DataDir = "./"
  IsArchival = true
  IsBeaconArchival = false
  IsOffline = false
  NoStaking = true
  NodeType = "explorer"
  ShardID = 0
```

`NoStaking = true` will verify if the BLS keys in your .hmy/blskeys folder are part of the original FN keys. You will need add in the folder dummy empty files and remove all others

```
# remove all keys, save it before if necessary
rm -f .hmy/blskeys/*
# create dummy files
touch .hmy/blskeys/bls.key
touch .hmy/blskeys/bls.pass
```

{% hint style="info" %}
IsBeaconArchival flag is applicable to explorer node only. For shard 1/2/3 the beacon shard 0 doesn't need to be in archival mode. So to save space, the recommendation is to set to false. For shard 0 explorer node, IsArchival flag will determine if the database is in archival mode or not.

DataDir (or --db\_dir below for cli flag) is the folder where the blockchain data will be store (ie location of harmony\_db\_0)
{% endhint %}

Alternatively, you can also run it using flag parsing:

```
./harmony --run=explorer --run.archive --run.shard=0 --db_dir=./
```

{% hint style="warning" %}
Make sure to follow the upgrading Explorer DB schema process [here](../upgrading-node/using-binary.md#non-validating-explorer-nodes) afterwards. This fixes a critical issue on Explorer DB.
{% endhint %}

## 2. Setup Systemd

{% hint style="info" %}
On this example, we will be installing the harmony daemon for user `harmony` on its home directory. Daemon will be configured with `sudo`but it will run with the `harmony`user at the end.
{% endhint %}

Create the `harmony.service` file:

```bash
sudo vi /etc/systemd/system/harmony.service
```

Add the content below to the file and save it. Change `User` to the local user you will be running the daemon and also `WorkingDirectory` to the home directory where you downloaded the harmony binary file previously. Parameter `ExecStart` needs to point to this same directory. On the example below we will be running the harmony binary using the `harmony.conf` file.

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
ExecStart=/home/harmony/harmony -c harmony.conf
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

To check your node follow instructions on [Checking A Node](../checking-node-status.md).
