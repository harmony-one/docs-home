---
description: >-
  Please note that right now we have two API versions v1 and v2, see the
  description below
---

# API

{% hint style="success" %}
**Complete documentation for Harmony's API's production API's can be found** [**here**](https://api.hmny.io/?version=latest) **including sample code and curl commands and code.** 
{% endhint %}

## Development Environments

[JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC) is a remote procedure call protocol encoded in JSON. You can use this API to access data from the Harmony nodes. The JSON-RPC API server runs on:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Chains</th>
      <th style="text-align:left">URLs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">mainnet</td>
      <td style="text-align:left"><a href="https://api.s0.t.hmny.io">https://api.s0.t.hmny.io</a> or <a href="https://api.harmony.one">https://api.harmony.one</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">testnet</td>
      <td style="text-align:left">
        <p><a href="https://api.s0.b.hmny.io">https://api.s0.b.hmny.io</a> or <a href="https://api.s0.pops.one">https://api.s0.pops.one</a> 
        </p>
        <p>(For Developers, Wallets, normal transaction)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">testnet</td>
      <td style="text-align:left">
        <p><a href="https://api.s0.backup1.b.hmny.io">https://api.s0.backup1.b.hmny.io</a> 
        </p>
        <p>(For indexers, bulk read/write transactions)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">localnet</td>
      <td style="text-align:left"><a href="http://localhost:9500">http://localhost:9500</a>
      </td>
    </tr>
  </tbody>
</table>

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

1. The prefix of RPC calls is different - **'hmy' for API v1** or **'hmyv2' for API v2** is used instead of 'eth'. Note that, Harmony also fully supports most `eth_` rpcs defined in [here](https://eth.wiki/json-rpc/API).
2. Address format: Harmony uses [bech32](https://en.bitcoin.it/wiki/Bech32) address format with `one1` prefix, however Ethereum style hex address can also be used. For example: `one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy` bech32 address is equivalent to `0x0B585F8DaEfBC68a311FbD4cB20d9174aD174016` hex address. Quick way to convert between formats is using explorer: [https://explorer.harmony.one/\#/address/one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy](https://explorer.harmony.one/#/address/one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy), at the top you will find "Address Format" ONE \| ETH options.
3. Harmony transactions are encoded using RLP, with two additional fields to represent from and to shard ids \(`shardID` and `toShardID`\), which is where it differs from Ethereum v1.

### API v1 and v2

1. **Harmony API has two versions**: **v1 with prefix 'hmy',** which returns hex numbers in API json response and **v2 with prefix 'hmyv2'** which mostly returns decimal numbers in API json response.
2. For each method which curl and response are different for API v1 and API v2: **there are two sections in description for API v1 and API v2** with examples. If there are no sections then examples are the same for v1 and v2 and can be quired both with 'hmy' prefix and 'hmyv2' prefix same way.
3. You can see in API response examples which variables **correspond to 0x format** and which to **decimal format**

