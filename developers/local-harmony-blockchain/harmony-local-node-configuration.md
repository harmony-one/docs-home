# Harmony Local Node Configuration

## Configuring your local node

{% hint style="info" %}
Pre-requisite is you have cloned and installed the harmony repository according to the [readme](https://github.com/harmony-one/harmony/blob/master/README.md).
{% endhint %}

### Configuration File Overview

* [debug.sh](https://github.com/harmony-one/harmony/blob/master/test/debug.sh) - This runs the local harmony node it runs deploy.sh with the following configuration
  * `./test/deploy.sh -D -1 ./test/configs/local-resharding.txt`
* [deploy.sh](https://github.com/harmony-one/harmony/blob/master/test/deploy.sh) - deploys the network
* [local-resharding.txt](https://github.com/harmony-one/harmony/blob/master/test/configs/local-resharding.txt) - defines the following for the network nodes
  * IP
  * Port
  * Node Type
  * wallet public address
  * BLS Signing Key public address
* [localnet.go](https://github.com/harmony-one/harmony/blob/master/internal/configs/sharding/localnet.go) - Configures epoch \(number of blocks between resharding\) as well as the sharding configurations. It leverages the configuration in localnodes.go
* [localnodes.go](https://github.com/harmony-one/harmony/blob/master/internal/genesis/localnodes.go) - Defines the initial \(and subsequent\) network configuration for the epochs

### Configuration Process

#### Current Local configuration

Following is the current local configuration

* Network - Local
* Shards - 2
* Nodes per shard \(Shards, Nodes, Internal\)
  * initially  - 2, 7, 5 
  * first - 2, 7, 5
  * second \(and final\) - 2, 10, 4
* Blocks per epoch - 10

## Running a local node

### Setting Environment Variables

Whenever starting a new terminal session you should start in the harmony folder and set your environment variables as follows

```text
cd /Users/johnwhitton/go/src/github.com/harmony-one/harmony
source ./scripts/setup_bls_build_flags.sh
```

### Running a node

```text
./scripts/go_executable_build.sh
./test/debug.sh
```

### Killing a running local node

```text
./test/kill_node.sh
```

### Checking Balances

```text
./bin/wallet -p local balances
```

