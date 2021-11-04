---
description: >-
  This section describes how to deploy a HRC20 smart contract on Harmony in
  1-minute.
---

# Deploy HRC20

## Overview

This section is designed to get the casual smart contract developer deploying HRC20 tokens (Harmony's ERC20 equivalent) on Harmony Network. **This can be done in under one Minute.**

This [github repository](https://github.com/harmony-one/H2O) contains the code and files used on this demo. You can also find many more examples that use HRC20 tokens on this [github repository](https://github.com/harmony-one/HRC).

### One Minute Deployment

Here is a short video running through the deployment:

{% embed url="https://www.youtube.com/watch?v=7zsLZYCvfb0" %}

### One Minute Instructions

```bash
npm install -g truffle@5.0.38
git clone https://github.com/harmony-one/H20.git
cd H20
cp .envSample .env
npm install
truffle compile
truffle migrate --network testnet --reset
truffle networks
```

### Interacting with Contracts

```javascript
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
