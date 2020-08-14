# Using Binary CLI

## 1. Download Binary CLI

Before we proceed to next steps we need to download the Binary CLI first:

```bash
curl -LO https://harmony.one/binary && mv binary harmony && chmod a+x harmony
```

The node can be setup using three different options. You **can choose** the option that fits you better:

### 1.1 Setup \(Using CLI Flags Parsing\)

You can run your Node Binary using CLI Flags Parsing:

{% tabs %}
{% tab title="Mainnet" %}
```bash
./harmony
```
{% endtab %}

{% tab title="" %}
```

```
{% endtab %}

{% tab title="Testnet" %}
```
./harmony --network testnet
```
{% endtab %}
{% endtabs %}

A full list of active flags as well as examples can be accessed through running the binary with `--help` option:

```text
./harmony --help
```

Output:

```text
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

### 1.2 Setup \(Using Config File\)

All the start options can be persisted and loaded from a single config file. To start a node, the following steps are also available**:**

1. Dump the default config.
2. Customize the config file.
3. Run harmony node with the config file.

#### 1.2.1 Dump the Default Config File

{% tabs %}
{% tab title="Mainnet" %}
```bash
./harmony dumpconfig harmony.conf
```
{% endtab %}

{% tab title="Testnet" %}
```
./harmony dumpconfig --network testnet harmony.conf
```
{% endtab %}
{% endtabs %}

A file `harmony.conf` is created and the default node options are set in the file in TOML formatting. Here is an example:

```text
Version = "1.0.0"

[BLSKeys]
  KMSConfigFile = ""
  KMSConfigSrcType = "shared"
  KMSEnabled = true
  KeyDir = "./.hmy/blskeys"
  KeyFiles = []
  MaxKeys = 10
  PassEnabled = true
  PassFile = ""
  PassSrcType = "auto"
  SavePassphrase = false

[General]
  DataDir = "./"
  IsArchival = false
  NoStaking = false
  NodeType = "validator"
  ShardID = -1

[HTTP]
  Enabled = true
  IP = "127.0.0.1"
  Port = 9500

[Log]
  FileName = "harmony.log"
  Folder = "./latest"
  RotateSize = 100
  Verbosity = 3

[Network]
  BootNodes = ["/ip4/100.26.90.187/tcp/9874/p2p/Qmdfjtk6hPoyrH1zVD9PEH4zfWLo38dP2mDvvKXfh3tnEv","/ip4/54.213.43.194/tcp/9874/p2p/QmZJJx6AdaoEkGLrYG4JeLCKeCKDjnFz2wfHNHxAqFSGA9","/ip4/13.113.101.219/tcp/12019/p2p/QmQayinFSgMMw5cSpDUiD9pQ2WeP6WNmGxpZ6ou3mdVFJX","/ip4/99.81.170.167/tcp/12019/p2p/QmRVbTpEYup8dSaURZfF6ByrMTSKa4UyUzJhSjahFzRqNj"]
  DNSPort = 9000
  DNSZone = "t.hmny.io"
  LegacySyncing = false
  NetworkType = "mainnet"

[P2P]
  KeyFile = "./.hmykey"
  Port = 9000

[Pprof]
  Enabled = false
  ListenAddr = "127.0.0.1:6060"

[TxPool]
  BlacklistFile = "./.hmy/blacklist.txt"

[WS]
  Enabled = true
  IP = "127.0.0.1"
  Port = 9800
```

The content of the config file can be modified for custom node start up command.

For example, to open the public HTTP RPCs, change the field `IP` under `[HTTP]` tag to `"0.0.0.0"`:

```text
[HTTP]
  Enabled = true
  IP = "0.0.0.0"
  Port = 9500
```

To run harmony internal nodes under legacy mode instead of staking mode, change the field `NoStaking` under `[General]` tag to `true`:

```text
[General]
  DataDir = "./"
  IsArchival = false
  NoStaking = true
  NodeType = "validator"
  ShardID = -1
```

#### 1.2.3 Start the node with Config File

Harmony node binary is able to start with options provided by the config file:

```text
./harmony -c harmony.conf
```

The values stored in the config file will be read and parsed to harmony as node start options.

### 1.3. Setup \(Using CLI Flags Parsing and a Config file combined\)

{% hint style="info" %}
If both config file and flag is provided, the node option stored in config file will be override by the values given in flag.
{% endhint %}

For example, In config file `harmony.conf`, HTTP server is enabled, and is open to public:

```text
[HTTP]
  Enabled = true
  IP = "0.0.0.0"
  Port = 9500
```

And a flag is also provided during the node start command to disable the HTTP server:

```text
./harmony -c harmony.conf --http=false
```

In this case, the command line flags will override the settings in the config file and thus the HTTP server is disabled.

```text
> curl localhost:9500
curl: (7) Failed to connect to localhost port 9500: Connection refused
```

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

