# Horizon Bridge SDK: Install & configure

### Install instructions

```
npm i bridge-sdk --save
```

## How to use

### 1. Init SDK instance

```js
const { BridgeSDK, TOKEN, EXCHANGE_MODE, STATUS } = require('bridge-sdk');
const configs = require('bridge-sdk/lib/configs');

const bridgeSDK = new BridgeSDK({ logLevel: 0 });

await bridgeSDK.init(configs.testnet);
```
#### You can set logLevel 0-2
```
0 - logs disabled
1 - only errors and success
2 - full log (errors, succees, info, panding, waiting etc)
```

#### You can use ```config.mainnet```: Harmony mainnet <> Ethereum mainnet.
#### Or you can use ```config.testnet```: Harmony testnet <> Ethereum Kovan testnet.
Also you can create config with your custom contracts and validators - like here https://github.com/harmony-one/ethhmy-bridge.sdk/blob/main/src/configs/mainnet.ts
