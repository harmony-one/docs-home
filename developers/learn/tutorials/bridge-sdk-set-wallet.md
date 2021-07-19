# Horizon Bridge SDK: set Wallet

### 2. Set user wallet (NodeJS mode)
#### For ONE -> ETH operation you need to add ONE wallet:
```js
await bridgeSDK.addOneWallet('bff5443377958e48e5fcfeb92511ef3f007ac5dd0a926a60b61c55f63098897e');
```

#### For ETH -> ONE operation you need to add Ethereum wallet:
```js
await bridgeSDK.addEthWallet('1111223395a5c3c1b08639b021f2b456d1f82e4bdd14310410dffb5f1277fe1b');
```

### 2.1. Set user wallet (Browser mode)
#### If you use Browser you can sign transactions with Metamask or OneWallet
#### Metamask:
```js
bridgeSDK.setUseMetamask(true);
```
full example here https://github.com/harmony-one/ethhmy-bridge.sdk/blob/main/examples/eth_to_one-browser.js

#### OneWallet:
```js
bridgeSDK.setUseOneWallet(true);
```
full example here https://github.com/harmony-one/ethhmy-bridge.sdk/blob/main/examples/eth_to_one-browser.js

#### MathWallet:
```js
bridgeSDK.setUseMathWallet(true);
```

If you want to do operations in both directions (eth <> one) - you need to set both wallet (Metamask + OneWallet).
