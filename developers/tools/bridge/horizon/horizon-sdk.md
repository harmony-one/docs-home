---
description: This page describes a simple example of using horizon bridge sdk.
---

# JS SDK

Horizon is Harmony's Ethereum bridge that can be used to bridge any ERC20, ERC721, and ETH from Ethereum to Harmony. Also, Harmony tokens like native ONE and HRC20 tokens can be bridged over to Ethereum. The mainnet bridge can be found in [https://bridge.harmony.one/](https://bridge.harmony.one) and testnet in [https://testnet.bridge.hmny.io/](https://testnet.bridge.hmny.io). General usage guide is provided in [Horizon guide](https://docs.harmony.one/home/general/horizon-bridge). The purpose of this doc is to use Horizon bridge SDK to bridge.

Horizon also supports bridging to Binance Smart Chain (BSC), however the BSC bridge sdk is still under development and should be available soon.

### Bridge Kovan BUSD to Harmony Testnet

The testnet bridge works from Kovan testnet to Harmony testnet. Kovan ETH can be obtained from [faucet](https://faucet.kovan.network). Harmony testnet ONE can be obtained from [faucet](https://docs.harmony.one/home/developers/network-and-faucets). Kovan BUSD can be obtained from [here](https://testnet.bridge.hmny.io/get-tokens). 

1\. Create a nodejs project and add `bridge-sdk` dependency.

```
mkdir sdk-test
cd sdk-test
npm init --yes
npm i bridge-sdk --save
```

2\. Create `test.js` file with code below.

```
const { BridgeSDK, TOKEN, EXCHANGE_MODE, STATUS } = require('bridge-sdk');
const configs = require('bridge-sdk/lib/configs');

const operationCall = async () => {
    // 2 - full logs, 1 - only success & errors, 0 - logs off
    const bridgeSDK = new BridgeSDK({ logLevel: 2 }); 
    
    await bridgeSDK.init(configs.testnet);
  
    await bridgeSDK.addEthWallet('cbcf3af28e37d8b69c4ea5856f2727f57ad01d3e86bec054d71fa83fc246f35b');
  
    let operationId;
  
    // display operation status
    let intervalId = setInterval(async () => {
      if (operationId) {
        const operation = await bridgeSDK.api.getOperation(operationId);
  
        if (operation.status !== STATUS.IN_PROGRESS) {
          clearInterval(intervalId);
        }
      }
    }, 4000);
  
    try {
      await bridgeSDK.sendToken(
        {
          type: EXCHANGE_MODE.ETH_TO_ONE,
          token: TOKEN.BUSD,
          amount: 0.01,
          oneAddress: 'one1we0fmuz9wdncqljwkpgj79k49cp4jrt5hpy49j',
          ethAddress: '0xc491a4c5c762b9E9453dB0A9e6a4431057a5fE54',
        },
        id => (operationId = id)
      );
    } catch (e) {
      console.log('Error: ', e.message);
    }
  
    process.exit();
  };
  
  operationCall();
```

3\. Run `node test.js` to test the bridge and see the transaction in [https://testnet.bridge.hmny.io/explorer](https://testnet.bridge.hmny.io/explorer)

Further documentation and several examples can be found in the [bridge-sdk github repo](https://github.com/harmony-one/ethhmy-bridge.sdk). The bridge UI widget is available to be used on your webapp [here](https://github.com/harmony-one/ethhmy-bridge.ui-sdk).
