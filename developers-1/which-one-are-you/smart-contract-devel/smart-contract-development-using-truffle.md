# Smart Contract Development using Truffle

## Setup

### Pre-requisites

The following tools should be installed for local Harmony Solidity development

```text
npm install -g truffle
```

### Initializing your codebase

Here we make an initial folder to create your smart contracts in. For more information you can refer to [truffle overview](https://www.trufflesuite.com/docs/truffle/overview).

```text
mkdir harmonyERC20
cd harmonyERC20
truffle init
```

### Installing Harmony Core

For deploying to Harmony you need to install [@harmony-js/core](https://www.npmjs.com/package/@harmony-js/core)

```text
npm install --save @harmony-js/core@next
npm install --save tslib
```

### Installing additional reference libraries

If developing standard ERC-20 or ERC-721 contracts than it is useful to install the [open zepplin libraries.](https://openzeppelin.com/contracts/)

```text
npm install openzeppelin-solidity -s
```

#### Installing Everything at once

For your convenience you can install all the dependencies by copying this [package.json](sample-files.md#package-json) and running `npm install`

### Configure truffle to use Harmony

To build against the Harmony instance you need to modify truffle\_config.js here is a sample [truffle\_config.js](sample-files.md#truffle_config-js) for the Harmony Network

### Fund your wallet

Ensure your account is funded.

### Add your contracts

We have included two contracts needed to deploy the Harmony ERC20 token. Simply copy these files into the contracts sub-folder

* [HarmonyMintable.sol](sample-files.md#harmonymintable-sol)
* [HarmonyERC20.sol](sample-files.md#harmonyerc-20-sol)

#### Add your migration file

Finally the migration file used to deploy HarmonyERC20.sol can be copied under the migrations sub\_folder

* [2\_deploy\_HarmonyERC20.js](sample-files.md#2_deploy_harmonyerc-20-js)

### Compile and deploy your contracts

The following commands are used to deploy the contract to testnet

```text
truffle compile
truffle migrate  --network testnet --reset
truffle networks
```

You should see the following

```text
Johns-MacBook-Pro:harmony-erc20 johnwhitton$ truffle compile

Compiling your contracts...
===========================
> Compiling ./contracts/HarmonyERC20.sol
> Artifacts written to /Users/johnwhitton/projects/sdk/harmony-erc20/build/contracts
> Compiled successfully using:
   - solc: 0.5.8+commit.23d335f2.Emscripten.clang

Johns-MacBook-Pro:harmony-erc20 johnwhitton$ truffle migrate  --network testnet --reset

Compiling your contracts...
===========================
> Compiling ./contracts/HarmonyMintable.sol
> Artifacts written to /Users/johnwhitton/projects/sdk/harmony-erc20/build/contracts
> Compiled successfully using:
   - solc: 0.5.8+commit.23d335f2.Emscripten.clang



Migrations dry-run (simulation)
===============================
> Network name:    'testnet-fork'
> Network id:      2
> Block gas limit: 0x66916c


1_initial_migration.js
======================

   Replacing 'Migrations'
   ----------------------
   > block number:        202311
   > block timestamp:     1569917046
   > account:             0x3aea49553Ce2E478f1c0c5ACC304a84F5F4d1f98
   > balance:             1073.236894617399407586
   > gas used:            246329
   > gas price:           2 gwei
   > value sent:          0 ETH
   > total cost:          0.000492658 ETH

   -------------------------------------
   > Total cost:         0.000492658 ETH


2_deploy_HarmonyERC20.js
========================

   Replacing 'HarmonyERC20'
   ------------------------
   > block number:        202313
   > block timestamp:     1569917053
   > account:             0x3aea49553Ce2E478f1c0c5ACC304a84F5F4d1f98
   > balance:             1073.233299613399407586
   > gas used:            1770479
   > gas price:           2 gwei
   > value sent:          0 ETH
   > total cost:          0.003540958 ETH

   -------------------------------------
   > Total cost:         0.003540958 ETH


Summary
=======
> Total deployments:   2
> Final cost:          0.004033616 ETH





Starting migrations...
======================
> Network name:    'testnet'
> Network id:      2
> Block gas limit: 0x66916c


1_initial_migration.js
======================

   Replacing 'Migrations'
   ----------------------
   > transaction hash:    0x2f2a03ffcf9d2e4fb9314d4e35360a4c9f0580a35efc791dd4e4c4d89ea7f1eb
   > Blocks: 0            Seconds: 4
   > contract address:    0xaE80fb77479Aa309831D411c2DC44F1EcFA703CC
   > block number:        202312
   > block timestamp:     1569917059
   > account:             0x3aea49553Ce2E478f1c0c5ACC304a84F5F4d1f98
   > balance:             1073.237125946399407586
   > gas used:            261329
   > gas price:           1 gwei
   > value sent:          0 ETH
   > total cost:          0.000261329 ETH


   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:         0.000261329 ETH


2_deploy_HarmonyERC20.js
========================

   Replacing 'HarmonyERC20'
   ------------------------
   > transaction hash:    0xdb1ab69342770ab559c41e5df32d255bce6f59584839fba8f181a9f08010dff8
   > Blocks: 0            Seconds: 4
   > contract address:    0x23d048d437615A346F9f50AcF051b0279B6d9bE2
   > block number:        202314
   > block timestamp:     1569917075
   > account:             0x3aea49553Ce2E478f1c0c5ACC304a84F5F4d1f98
   > balance:             1073.235223444399407586
   > gas used:            1860479
   > gas price:           1 gwei
   > value sent:          0 ETH
   > total cost:          0.001860479 ETH


   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:         0.001860479 ETH


Summary
=======
> Total deployments:   2
> Final cost:          0.002121808 ETH



Johns-MacBook-Pro:harmony-erc20 johnwhitton$ truffle networks

Network: UNKNOWN (id: 5777)
  HarmonyERC20: 0x6C061Ff6624c408d4A7b09704c853fa26D4C6218
  Migrations: 0x8AEF5F5A61420777fcfB2F3313a77292C66fb3B1

Network: development (id: 2)
  No contracts deployed.

Network: testnet (id: 2)
  HarmonyERC20: 0x23d048d437615A346F9f50AcF051b0279B6d9bE2
  Migrations: 0xaE80fb77479Aa309831D411c2DC44F1EcFA703CC

Johns-MacBook-Pro:harmony-erc20 johnwhitton$
```

### Your contract is now available at

```text
0x23d048d437615A346F9f50AcF051b0279B6d9bE2
```

