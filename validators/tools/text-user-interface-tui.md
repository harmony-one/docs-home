---
description: Text based user interface for Harmony node.
---

# Text User Interface \(TUI\)

## Harmony TUI

Text based user interface for Harmony node.  
Below information is currently displayed on Harmony-TUI

1. **Section - Harmony Blockchain** - _\*\*_Connected peers - Leader's one address - Current epoch number - Recent timestamps of various stages
2. **Section - Harmony Node** - _\*\*_Harmony node binary version - ShardId of local node - Balance of user's one account
3. **Section - Current Block** - _\*\*_Current block number - Size of current block in bytes - Hash of current block - StateRoot - BlockEpoch - Number of signers who signed last block
4. **Section - System Stats** - CPU usage in percentage - Memory/RAM usage of system - Used disk space
5. **Section - Validator Logs** This section shows validator log file

## Dependencies

1. harmony node running on localhost:9000
2. shared libraries required for running harmony node
3. Harmony TUI binary should be in same directory as harmony node binary

## Build and run harmony-tui binary

**Build from source code**

1. Clone repository - `git clone git@github.com:harmony-one/harmony-tui.git`
2. `cd harmony-tui`
3. Invoke `make` to build `harmony-tui` binary for local platform or `make build-linux` for linux
4. binary will get generated in `./bin` directory
5. Copy harmony-tui binary from `./bin` to the same directory as harmony node binary
6. Invoke binary - `path_to_binary/harmony-tui --address=YOUR_ONE_ADDRESS`

**Download binary and run .**

1. Download binary directly from [here](http://harmony.one/tui).
2. Place downloaded binary in same directory as harmony node binary
3. Invoke binary - `path_to_binary/harmony-tui --address=YOUR_ONE_ADDRESS`

## Usage

1. Invoke binary - `path_to_binary/harmony-tui --address=YOUR_ONE_ADDRESS`
2. Help information - `path_to_binary/harmony-tui--help`
3. Command line arguments supported by harmony-tui binary  
   `-address string`

   ```text
       `address of your one account (default "Not Provided")`
   ```

   `-env string`

   ```text
       `environment of system binary is running on option 1- "local" option 2- "ec2" (default "ec2")`
   ```

   `-version`

   ```text
       `version of the binary`
   ```

**Examples**

1. Run binary - `path_to_binary/harmony-tui --address=YOUR_ONE_ADDRESS --env=local`
2. Check version - `path_to_binary/harmony-tui --version`

## Sample screenshot​[​](https://raw.githubusercontent.com/harmony-one/harmony-tui/master/doc/images/tui-sample.gif?token=AEY7S2JV6DIWLODPOXCKMN25VED6W) <a id="sample-screenshot"></a>

![](https://raw.githubusercontent.com/harmony-one/harmony-tui/master/doc/images/tui-sample.gif?token=AEY7S2JV6DIWLODPOXCKMN25VED6W)

