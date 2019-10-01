# Smart Contracts development using Truffle

## Setup

### Pre-requisites

The following tools should be installed for local Harmony Solidity development

```text
npm install -g truffle
```

### Initializing your codebase

Here we make an initial folder to create your smart contracts in. For more information you can refer to [truffle overview](https://www.trufflesuite.com/docs/truffle/overview).

```text
mkdir harmony-erc20
cd harmony-erc20
truffle init
yarn install tslib
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

### Configure truffle to use Harmony

To build against the Harmony instance you need to modify truffle\_config.js to use [this version](untitled.md).

### Fund your wallet

Ensure your account is funded see [Funding your wallet]().

### Compile and deploy your contracts

```text
truffle compile
truffle migrate
truffle networks
```

You should see the following

```text
johns-mbp:contract-library johnwhitton$ truffle compile

Compiling your contracts...
===========================
> Compiling ./contracts/Migrations.sol
> Artifacts written to /Users/johnwhitton/projects/sdk/contract-library/build/contracts
> Compiled successfully using:
   - solc: 0.5.8+commit.23d335f2.Emscripten.clang

johns-mbp:contract-library johnwhitton$ truffle migrate

Compiling your contracts...
===========================
> Everything is up to date, there is nothing to compile.


Migrations dry-run (simulation)
===============================
> Network name:    'development-fork'
> Network id:      1
> Block gas limit: 0x18328df


1_initial_migration.js
======================

   Deploying 'Migrations'
   ----------------------
   > block number:        1727
   > block timestamp:     1565071883
   > account:             0x3aea49553Ce2E478f1c0c5ACC304a84F5F4d1f98
   > balance:             99.9911632848
   > gas used:            246329
   > gas price:           2 gwei
   > value sent:          0 ETH
   > total cost:          0.000492658 ETH

   -------------------------------------
   > Total cost:         0.000492658 ETH


Summary
=======
> Total deployments:   1
> Final cost:          0.000492658 ETH


Starting migrations...
======================
> Network name:    'development'
> Network id:      1
> Block gas limit: 0x18328df


1_initial_migration.js
======================

   Deploying 'Migrations'
   ----------------------
   > transaction hash:    0x587058b91157af0f639b719d0daf787f3066830ed39aadc61d66ed7f87f04363
   > Blocks: 0            Seconds: 0
   > contract address:    0xfA63aa1B35AbEa20e880778A0Bd9657172Ee6051
   > block number:        1726
   > block timestamp:     1565071884
   > account:             0x3aea49553Ce2E478f1c0c5ACC304a84F5F4d1f98
   > balance:             99.9911332848
   > gas used:            261329
   > gas price:           2 gwei
   > value sent:          0 ETH
   > total cost:          0.000522658 ETH


   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:         0.000522658 ETH


Summary
=======
> Total deployments:   1
> Final cost:          0.000522658 ETH

johns-mbp:contract-library johnwhitton$ truffle networks

Network: development (id: 1)
  Migrations: 0xfA63aa1B35AbEa20e880778A0Bd9657172Ee6051
```

### Your contract is now available at

```text
0xfA63aa1B35AbEa20e880778A0Bd9657172Ee6051
```

