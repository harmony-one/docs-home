# Envio

[Envio](https://envio.dev/) is a feature-rich indexing solution that provides developers with a seamless and efficient way to index and aggregate real-time or historical blockchain data for any EVM. The indexed data is easily accessible through custom GraphQL queries, providing developers with the flexibility and power to retrieve specific information.

Envio offers native support for Harmony (both testnet and mainnet) and has been designed to support high-throughput blockchain applications that rely on real-time data for their business requirements.

Designed to optimize the user experience, Envio offers automatic code generation, flexible language support, quickstart templates, and a reliable cost-effective [hosted service](https://docs.envio.dev/docs/hosted-service).

Indexers on Envio can be written in JavaScript, TypeScript, or ReScript.

## Envio HyperSync 

Envio supports [HyperSync](https://docs.envio.dev/docs/hypersync) on Harmony mainnet. 

HyperSync is an accelerated data query layer for the Harmony blockchain, providing APIs that bypass JSON-RPC for 20-100x faster syncing of historical data. HyperSync is used by default in Envio's indexing framework, with the use of RPC being optional. Using HyperSync, application developers do not need to worry about RPC URLs, rate-limiting, or managing infrastructure and can easily sync large datasets in a few minutes, something that would usually take hours or days using RPC.

HyperSync is also available as a standalone API for data analytic use cases. Data analysts can interact with the HyperSync API using JavaScript, Python, or Rust clients and extract data in JSON, Arrow, or Parquet formats. For more information, visit the HyperSync documentation [here](https://docs.envio.dev/docs/overview-hypersync).


## Key Features 

- Contract Import: Autogenerate the key boilerplate for an entire Indexer project off a single or multiple smart contracts. Deploy within minutes. 

- Multi-chain Support: Aggregate data across multiple networks into a single database. Query all your data with a unified GraphQL API. 

- Asynchronous Mode: Fetch data from off-chain storage such as IPFS, or contract state (e.g. smart contract view functions).

- Quickstart Templates: Use pre-defined indexing logic for popular OpenZeppelin contracts (e.g. ERC-20).


## Getting Started

Users can choose whether they want to start from a quickstart template, perform a subgraph migration, or use the contract import feature. 

The following files are required from the user to run the Envio indexer:

- Configuration (defaults to `config.yaml`)
- GraphQL Schema (defaults to `schema.graphql`)
- Event Handlers (defaults to `src/EventHandlers.*` depending on the language chosen)

These files are auto-generated according to the template and language chosen by running the `envio init` command. 

## Contract Import Tutorial

This walkthrough explains how to initialize an indexer using a single or multiple contracts that are already deployed on a blockchain. This process allows a user to quickly and easily start up a basic indexer and a queryable GraphQL API for their blockchain application within a few minutes.

### Intialize your indexer

`cd` into the folder of your choice and run

```bash
envio init
```

Name your indexer

```bash
? Name your indexer:
```

Choose the directory where you would like to setup your project (default is the current directory)

```bash
? Set the directory:  (.) .
```

Select `Contract Import` as the initialization option.

```bash
? Choose an initialization option
  Template
  SubgraphMigration
> ContractImport
[↑↓ to move, enter to select, type to filter]
```

```bash
? Would you like to import from a block explorer or a local abi?
  Block Explorer
> Local ABI
[↑↓ to move, enter to select, type to filter]
```

Block Explorer option only requires user to input the contracts address and chain of the contract. If the contract is verified and deployed on one of the supported chains, this is the quickest setup as it will retrieve all needed contract information from a block explorer. 

Please note: Block explorer option currently only supports networks with etherscan. If the network doesnt have etherscan, you can proceed using the Local ABI option. 

Choosing `Local ABI` option will allow you to point to a JSON file containing the smart contract ABI.
The `Contract Import` process will then populate the required files from the ABI.

#### Specify the directory of JSON file containing ABI

```bash
? What is the path to your json abi file?
```

#### Choose which events to include in the `config.yaml` file

```bash
? Which events would you like to index?
> [x] ClaimRewards(address indexed from, address indexed reward, uint256 amount)
  [x] Deposit(address indexed from, uint256 indexed tokenId, uint256 amount)
  [x] NotifyReward(address indexed from, address indexed reward, uint256 indexed epoch, uint256 amount)
  [x] Withdraw(address indexed from, uint256 indexed tokenId, uint256 amount)
[↑↓ to move, space to select one, → to all, ← to none, type to filter]
```

#### Specify which chain the contract is deployed on

```bash
? Choose network:
> <Enter Network Id>
  ethereum-mainnet
  goerli
  optimism
  base
  bsc
  harmony
v polygon
[↑↓ to move, enter to select, type to filter]
```

#### Enter in the name for the contract

```bash
? What is the name of this contract?
```

#### Enter in the address of the contract

```bash
? What is the address of the contract?
[Use the proxy address if your abi is a proxy implementation]
```

Note if you are using a proxy contract with an implementation, the address should be for the proxy.

#### Select the continuation option

```bash
? Would you like to add another contract?
> I'm finished
  Add a new address for same contract on same network
  Add a new network for same contract
  Add a new contract (with a different ABI)
[Current contract: BribeVotingReward, on network: harmony]
```

The `Contract Import` process will prompt the user whether they would like to finish the import process or continue adding more addresses for same contract on same network, addresses for same contract on different network or a different contract.

For more information on contract import feature, visit the documentation [here](https://docs.envio.dev/docs/contract-import).


## Envio Indexer Examples

Click [here](https://docs.envio.dev/docs/example-uniswap-v3) for Envio Indexer Examples.

## Getting Help

Indexing can be a rollercoaster, especially for more complex use cases. Our engineers are available to help you with your data availability needs.

Join our growing community of elite builders, and find peace of mind with Envio. 

* [Discord](https://discord.gg/mZHNWgNCAc)
* Email: [hello@envio.dev](mailto:hello@envio.dev)

