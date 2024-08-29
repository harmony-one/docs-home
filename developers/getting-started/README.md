---
description: A quick guide to getting started with developing on Harmony blockchain.
---

# Getting Started

## Overview

Harmony is a powerful blockchain that is EVM compatible with sharding and [staking](https://docs.harmony.one/home/validators) features. Developing on Harmony should feel very familiar for Ethereum developers, as Harmony is [fully Ethereum compatible](https://medium.com/harmony-one/launching-full-ethereum-compatibility-on-harmony-e181ed3c6a24) and inherits almost all the tools and libraries from Ethereum, like truffle, remix, web3js, etc.

The simplest way to interact with Harmony blockchain is via JSON RPCs.

#### Querying Harmony blockchain using JSON RPCs

* JSON [RPCs](https://docs.harmony.one/home/developers/api) and `curl` command [examples](https://docs.harmony.one/home/developers/api/methods)

To really explore the full potential of Harmony blockchain, creating a wallet is the next step.

#### Creating a wallet (or ONE address)

* Using [MetaMask](https://docs.harmony.one/home/general/wallets/browser-extensions-wallets/metamask-wallet) or [mathwallet](https://docs.harmony.one/home/wallets/browser-extensions-wallets/mathwallet) browser extensions. Any other [wallets](https://docs.harmony.one/home/wallets) can also be used.
* Harmony [CLI](https://docs.harmony.one/home/wallets/harmony-cli), also provides a quick way to create/manage wallet, interact with blockchain, etc.

{% hint style="info" %}
Harmony uses [bech32](https://en.bitcoin.it/wiki/Bech32) address format with `one1` prefix, however Ethereum style hex address can also be used. For example: `one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy` bech32 address is equivalent to `0x0B585F8DaEfBC68a311FbD4cB20d9174aD174016` hex address. Quick way to convert between formats is using explorer: [https://explorer.harmony.one/#/address/one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy](https://explorer.harmony.one/#/address/one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy), at the top you will find "ONE / ETH address" options.
{% endhint %}

#### Development environments

* Several development environments exists: [mainnet, testnnet, localnet](https://docs.harmony.one/home/developers/api#development-environments)
* Testnet faucet
  * [https://faucet.pops.one](https://faucet.pops.one/)&#x20;
  * [https://chaindrop.org](https://chaindrop.org/)&#x20;
* Blockchain Explorers
  * Mainnet: [https://explorer.harmony.one](https://explorer.harmony.one/)&#x20;
  * Testnet: [https://explorer.testnet.harmony.one](https://explorer.testnet.harmony.one/)

We provide SDKs in several different languages. However most feature complete is our JavaScript SDK, which is the preferred language for DApp development.

{% hint style="success" %}
Feel free to ping any POPS member for issues on the testnet network/explorer/faucet on harmony discord @harmony-pops or telegram [P-OPS Team Validator](https://t.me/POPS\_Team\_Validator)\
Faucet can also be refilled by anyone by sending fund back to the contract address shown on [https://faucet.pops.one](https://faucet.pops.one)
{% endhint %}

#### Using SDKs to interact with Harmony blockchain

* About [SDKs](https://docs.harmony.one/home/developers/sdk)
* The most popular is our [JavaScript SDK](https://github.com/harmony-one/sdk), which includes examples, documentation, and DApps developed in previous hackathons
* Other SDKs include: Golang CLI, Java SDK, Python SDK
  * Note that, the Python SDK has only read-only features, meaning no transaction signing or smart contracts

### How to deploy a smart contract on Harmony?

* [Tutorial](https://docs.harmony.one/home/developers/deploying-on-harmony)
* [Github repo](https://github.com/harmony-one/Smart-Contract-Demo)
* [Interacting with wallets programmatically](https://docs.harmony.one/home/developers/interacting-with-wallet-extensions)

### How to create a simple DApp on Harmony?

One of the best ways to get started is to use [scaffold-eth](https://github.com/austintgriffith/scaffold-eth) which now has integrated Harmony support.

{% embed url="https://youtu.be/ShJZf5lsXiM" %}

You can also use the [Harmony DApp template generator](https://github.com/harmony-one/harmony-dapp-template) to get started.

{% embed url="https://www.youtube.com/watch?v=ys7dtz1YvpM" %}

* [Tutorial](https://www.youtube.com/watch?v=1eigt2z8oWM\&t=4s)
* [GitHub repo](https://github.com/harmony-one/token-faucet-demo-dapp)

Many other examples and DApps can be found in the [SDK repo](https://github.com/harmony-one/sdk) and under [showcases](https://docs.harmony.one/home/showcases).

### Resources

* [talk.harmony.one](https://talk.harmony.one/c/developers/31) - for reporting issues, asking questions, or interact with other developers
* Harmony [GitHub](https://github.com/harmony-one)
* Harmony dev [Reddit](https://www.reddit.com/r/Harmony\_Devs/)
* Discord channels: [#developers](https://discord.gg/bK3vb3chuv), [#development](https://discord.gg/Umfnga3bFU)
* Harmony dev [Telegram](https://t.me/HarmonyDevs)

### Known Limitations

* **Only cross-shard native token (ONE token) transfers** are allowed. No cross-shard for HRC20 or other contracts. Meaning, smart contracts are deployed on shard-0 and all contract interactions happen on shard-0. Contracts can still be deployed on other shards, however they won't be able to interact with contracts in other shards. We have cross-shard smart contract on our roadmap for 2023.
