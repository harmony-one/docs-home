# Smart Contract Developer

## Overview

This section is designed to get the casual smart contract developer up and running deploying ERC20 tokens on a harmony network. **This can be done in under one Minute.**

### One Minute Deploy

Here is a short video running through the deployment.

{% embed url="https://www.youtube.com/watch?v=7zsLZYCvfb0" caption="" %}

### One Minute Instructions

```text
npm install -g truffle@5.0.38
git clone https://github.com/harmony-one/H2O.git
cd H2O
npm install
truffle compile
truffle migrate --network testnet --reset
truffle networks
```

### Interacting with contracts

```text
truffle console --network testnet
truffle(testnet)> HarmonyERC20.deployed().then(function(instance){myHRC20=instance})
undefined
truffle(testnet)> myHRC20.symbol()
'H20'
truffle(testnet)> myHRC20.name()
'HarmonyERC20'
truffle(testnet)> myHRC20.decimals()
BN { negative: 0, words: [ 18, <1 empty item> ], length: 1, red: null }
truffle(testnet)> myHRC20.totalSupply()
BN {
  negative: 0,
  words: [ 16777216, 62077800, 20718012, 3, <1 empty item> ],
  length: 4,
  red: null
}
```

### Detailed Overview

For detailed instructions, sample files and github repository please see below

* [Smart Contract Development Using Truffle](smart-contract-development-using-truffle.md)
* [Sample Files](sample-files.md)
* [H2O github repository](https://github.com/harmony-one/H2O)

