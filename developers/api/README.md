---
description: >-
  Please note that right now we have two API versions v1 and v2, see the
  description below
---

# API

{% hint style="success" %}
**Complete documentation for Harmony's API's can be found** [**here**](https://api.os.hmny.io/) **including sample code and curl commands and code.** 
{% endhint %}

## Development Environments

[JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC) is a remote procedure call protocol encoded in JSON. You can use this API to access data from the Harmony nodes. The JSON-RPC API server runs on:

| Chains | URLs |
| :--- | :--- |
| mainnet | [https://api.s0.t.hmny.io](https://api.s0.t.hmny.io) |
| testnet | [https://api.s0.b.hmny.io](https://api.s0.pga.hmny.io) |
| localnet | [http://localhost:9500](http://localhost:9500) |

Web sockets can also be used

| Chains | URLs |
| :--- | :--- |
| mainnet | [wss://ws.s0.t.hmny.io](wss://ws.s0.t.hmny.io) |
| testnet | [wss://ws.s0.b.hmny.io](wss://ws.s0.pga.hmny.io) |
| localnet | [wss://localhost:9800](./) |

All requests follow the standard JSON-RPC format and include 4 variables in the data object:

| Request Data Object | Example | Purpose |
| :--- | :--- | :--- |


| jsonrpc | "2.0" | Specifies version number |
| :--- | :--- | :--- |


| method | "hmy\_getBalance" | Method to be called server-side |
| :--- | :--- | :--- |


| params | \["0xD7Ff...24Cf2d", "latest"\] | Parameters for method call |
| :--- | :--- | :--- |


### Key Differences between Harmony and Ethereum

1. The prefix of RPC calls is different - **'hmy' for API v1** or **'hmyv2' for API v2** is used instead of 'eth'.
2. Address format, SDK uses two, the default use checksum, it is recommended to use Bech32. has been defined in the SDK.
3. Transaction uses RLP, but adds two fields, one is shardID and the other is toShardID.
4. There are some RPC Ethereum, there is no Harmony, we will discuss it in detail during the process.

### API v1 and v2

1. **Harmony API has two versions**: **v1 with prefix 'hmy',** which returns hex numbers in API json results and **v2 with prefix 'hmyv2'** which mostly returns decimal numbers in API json results.
2. For each method which curl and response are different for API v1 and API v2: **there are two sections in description for API v1 and API v2** with examples. If there are no sections then examples are the same for v1 and v2 and can be quired both with 'hmy' prefix and 'hmyv2' prefix same way.
3. You can see in API response examples which variables **correspond to 0x format** and which to **decimal format**

So for the JS project, you can directly modify the existing Ethereum library, or you can use the SDK package to see your engineering needs.

**The best practice is to extend the SDK's Transaction class and then add customization.**

The biggest difference is that Harmony does not use `eth_sendTransaction` and uses `eth_sendRawTransaction` to send the signed bytes, this is called `hmy_sendRawTransaction`.

