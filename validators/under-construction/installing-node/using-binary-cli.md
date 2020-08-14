# Using Binary CLI

## 1. Download Binary CLI

Before we proceed to next steps we need to download the Binary CLI first:

```bash
curl -LO https://harmony.one/binary && mv binary harmony && chmod a+x harmony
```

The Harmony Binary CLI can be setup using three different options. You can choose the option that fits you better.

### 1. Setup \(Using CLI Flags Parsing\)

You can run your Node Binary using CLI Flags Parsing:

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

A full list of active flags as well as examples can be access through running binary with `--help` option:

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

### 2. Setup \(Using Config file\)

### 3. Setup \(Using CLI Flags Parsing and a Config file combined\)

## 2. Setup Systemd Service

