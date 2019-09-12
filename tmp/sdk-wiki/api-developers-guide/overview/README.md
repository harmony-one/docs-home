# Introduction

## Development Environments

[JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC) is a remote procedure call protocol encoded in JSON. You can use this API to access data from the Harmony nodes. The JSON-RPC API server runs on:

| Chains | URLs |
| :--- | :--- |
| mainnet | TBD |
| betaNet | http://l0.b.hmny.io:9500 |
| local | http://localhost:9500 |

All API calls are POST requests.

All requests follow the standard JSON-RPC format and include 4 variables in the data object:

| Request Data Object | Example |
| :--- | :--- |
| jsonrpc | "2.0" |
| method | "hmy\_getBalance" |
| params | \["0xD7Ff41CA29306122185A07d04293DdB35F24Cf2d", "latest"\] |
| id | "1" |

**Sample Request body**`{"jsonrpc":"2.0","method":"hmy_getBalance","params":["0xD7Ff41CA29306122185A07d04293DdB35F24Cf2d", "latest"],"id":1}`

## Following is a list of Key Harmony Repositories

Harmony.one github - [https://github.com/harmony-one](https://github.com/harmony-one)  
Harmony Blockchain Repository - [https://github.com/harmony-one/harmony](https://github.com/harmony-one/harmony)  
Harmony SDK - [https://github.com/harmony-one/sdk](https://github.com/harmony-one/sdk)  
Harmony DApp Examples - [https://github.com/harmony-one/dapp-examples](https://github.com/harmony-one/dapp-examples)  
Harmony Web Wallet \(WIP\) - [https://github.com/harmony-one/dapp-examples/tree/master/web/WebWallet](https://github.com/harmony-one/dapp-examples/tree/master/web/WebWallet)

## Key Differences Harmony and Ethereum

1. The prefix of rpc is different, 'hmy' instead of 'eth'.
2. Address format, sdk uses two, the default use checksum, it is recommended to use bech32. has been defined in the SDK.
3. Transaction uses rlp, but adds two fields, one is shardID and the other is toShardID.
4. There are some rpc Ethereum, there is no harmony, we will discuss it in detail during the process.

So for the JS project, you can directly modify the existing Ethereum library, or you can use the SDK package to see your engineering needs.

**The best practice is to extend the SDK's Transaction class and then add customization.**

The biggest difference is that Harmony does not use `eth_sendTransaction` and uses `eth_sendRawTransaction` to send the signed bytes, this is called `hmy_sendRawTransaction`.



