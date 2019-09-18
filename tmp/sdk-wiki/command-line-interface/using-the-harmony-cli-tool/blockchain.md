---
description: Interacting with the Harmony blockchain
---

# Blockchain

### Available actions

Here is the top level entry point of the `blockchain` subcommand for `hmy_cli`

```text
./hmy_cli blockchain

Query Harmony's blockchain for high level metrics, queries

Usage:
  hmy_cli blockchain [flags]
  hmy_cli blockchain [command]

Available Commands:
  balance                Retreive balance for account
  block-by-number        Get a harmony blockchain block by block number
  protocol-version       The version of the Harmony Protocol
  transaction-by-hash    Get transaction by hash
  transaction-by-receipt Get transaction by receipt
  transaction-count      Get a transaction's count

Flags:
  -h, --help          help for blockchain
  -l, --latest        Use latest in query
      --node string   <host>:<port> (default "http://localhost:9500")

Global Flags:
  -p, --pretty   pretty print JSON outputs

Use "hmy_cli blockchain [command] --help" for more information about a command.
```



