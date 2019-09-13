# Running a Local Node

## Setting Environment Variables

Whenever starting a new terminal session you should start in the harmony folder and set your environment variables as follows

```text
cd /Users/johnwhitton/go/src/github.com/harmony-one/harmony
source ./scripts/setup_bls_build_flags.sh
```

## Building the executables

```text
./scripts/go_executable_build.sh
```

## Running a node

```text
./test/debug.sh
```

## Killing a running local node

```text
./test/kill_node.sh
```

## Checking Balances

```text
./bin/wallet -p local balances
```

