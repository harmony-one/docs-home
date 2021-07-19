# Horizon Bridge SDK: Send tokens in Step by Step mode

Interacting with the bridge in a step-by-step mode means that you must call the sdk methods in a specific sequence and wait for their successful completion.
These methods is available in bridge-sdk since version 2.

### Step by Step example 

We skipped call contract methods step in this example and will assume that you already have a successfully completed Locked Tokens transaction

https://github.com/harmony-one/ethhmy-bridge.sdk/blob/main/examples/version_2/eth_to_one-node.js

```js
const { BridgeSDK, TOKEN, EXCHANGE_MODE, STATUS } = require('bridge-sdk');
const configs = require('bridge-sdk/lib/configs');

const operationCall = async () => {
  const bridgeSDK = new BridgeSDK({ logLevel: 2 }); // 2 - full logs, 1 - only success & errors, 0 - logs off

  await bridgeSDK.init(configs.testnet);

  try {
    const operation = await bridgeSDK.createOperation({
      type: EXCHANGE_MODE.ETH_TO_ONE,
      token: TOKEN.BUSD,
      amount: 0.01,
      oneAddress: 'one1we0fmuz9wdncqljwkpgj79k49cp4jxxxx',
      ethAddress: '0xc491a4c5c762b9E9453dB0A9e6a4431xxxxx',
    });

    /********/
    // Here you need to generate and call contract methods to lock your token
    // We skipped this step in this example and will assume that you already have a successfully completed Locked Tokens transaction.
    /********/

    await operation.skipAction(ACTION_TYPE.approveEthManger);

    await operation.confirmAction({
      actionType: ACTION_TYPE.lockToken,
      transactionHash: '0x61b125de7560069aef96530ef9430715e3807f41a71056fxxxxxx',
    });
  } catch (e) {
    console.error('Error: ', e.message, e.response?.body);
  }
};

operationCall();
```

### You can see more examples here
https://github.com/harmony-one/ethhmy-bridge.sdk/blob/main/examples/version_2
