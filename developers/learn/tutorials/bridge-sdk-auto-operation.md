# Horizon Bridge SDK: Send tokens in auto mode

### 3. Send tokens
```js
let oprationId;

try {
  await bridgeSDK.sendToken({
    type: EXCHANGE_MODE.ETH_TO_ONE,
    token: TOKEN.BUSD,
    amount: 0.01,
    oneAddress: 'one11234dzthq23n58h43gr4t52fa62rutx4s247sk',
    ethAddress: '0x12344Ab6773925122E389fE2684A9A938043f475',
  }, (id) => oprationId = id);
} catch (e) {
  console.log(e.message);
}
```
You don't need to do anything more. All other actions will be done automaticly. If you work in browser mode - sign transactions action also will be called automaticly. You need only to fetch and display operation status (step 4)

#### * if you want to send ERC20 token - you need to set token ````token: TOKEN.ERC20```` and add one more param ``erc20Address: 0x...``

#### * Use try-catch to catch error with reason message. Also you can set logLevel = 2 for better debugging (look at step 1).

### 4. Get operation details

```js
const operation = await bridgeSDK.api.getOperation(operationId);
```
#### * Recommended to use this call in a cycle if you want to monitoring & display operation status (look at full example)
###
## Eth -> One (full example)

https://github.com/harmony-one/ethhmy-bridge.sdk/blob/main/examples/eth_to_one-node.js

```js
const { BridgeSDK, TOKEN, EXCHANGE_MODE, STATUS } = require('bridge-sdk');
const configs = require('bridge-sdk/lib/configs');

const operationCall = async () => {
    const bridgeSDK = new BridgeSDK({ logLevel: 2 }); // 2 - full logs, 1 - only success & errors, 0 - logs off

    await bridgeSDK.init(configs.testnet);

    await bridgeSDK.addEthWallet('cbcf3af28e37d8b69c4ea5856f2727f57ad01d3e86bec054d71fa83fc246f35b');

    let operationId;

    // display operation status
    let intervalId = setInterval(async () => {
        if (operationId) {
            const operation = await bridgeSDK.api.getOperation(operationId);

            /*
            console.log(operation.status);
            console.log(
              'Action: ',
              operation.actions.filter(a => a.status === STATUS.IN_PROGRESS)
            );
            */

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

### You can see more examples here
https://github.com/harmony-one/ethhmy-bridge.sdk/tree/main/examples

* If you want to copy this this example sources to your project - you need to change:
```js
const { BridgeSDK, TOKEN, EXCHANGE_MODE, STATUS } = require('..');
const configs = require('../lib/configs');
```
to
```js
const { BridgeSDK, TOKEN, EXCHANGE_MODE, STATUS } = require('bridge-sdk');
const configs = require('bridge-sdk/lib/configs');
```


## More API methods

### getOperations
```js
const operations = await bridgeSDK.api.getOperations({ size: 50, page: 0 });
```
