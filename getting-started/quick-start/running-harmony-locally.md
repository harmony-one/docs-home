# Running Harmony Locally

## Deploying from Source - Mac

To deploy from source code follow the instructions in [harmony readme](https://github.com/harmony-one/harmony/blob/master/README.md) to install the codebase

Below is a sample deployment after the codebase has been built

```
source ./scripts/setup_bls_build_flags.sh
./scripts/go_executable_build.sh 
./test/debug.sh 
```

### Configuration Paramaters

1. Number of Shards `localnetEpochBlock1 = 100000000000000000`
2. Number of Nodes
3. Internal vs External Nodes
4. Resharding configuration
5. Time between epochs

