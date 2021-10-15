# Setup

### Pre-Requisites

The following tools need to be installed:

* [NodeJS v12+](https://nodejs.org/en/download/)
* Node Package Manager (npm)

### Globally Truffle Installation

```bash
npm install -g truffle     
```

{% hint style="info" %}
 You might be require to provide super user privileges to install it.
{% endhint %}

### Project Setup

Navigate to the directory where you want to setup you project. For this guide we will be using "demo" as the project name.

```bash
truffle init demo
cd demo
```

### Installing Dependencies

```bash
npm install --save @harmony-js/core
npm install --save @harmony-js/utils
npm install --save tslib
npm install --save dotenv
```

(Optional) Install Additional Dependencies if required. We wont be using this for this demo.

```bash
npm install openzeppelin-solidity -s
```

Create a `.env` file in the project root directory and put your mnemonic code, private key, and rpc url in it. We will be using the following structure for our demo.

```
//LOCAL
LOCAL_PRIVATE_KEY=<YOUR_PRIVATE_KEY>
LOCAL_MNEMONIC=<YOUR_MNEMONIC_CODE>
LOCAL_0_URL='http://localhost:9500'

//TESTNET
TESTNET_PRIVATE_KEY=<YOUR_PRIVATE_KEY>
TESTNET_MNEMONIC=<YOUR_MNEMONIC_CODE>
TESTNET_0_URL='https://api.s0.b.hmny.io'
TESTNET_1_URL='https://api.s1.b.hmny.io'

//MAINNET
MAINNET_PRIVATE_KEY=<YOUR_PRIVATE_KEY>
MAINNET_MNEMONIC=<YOUR_MNEMONIC_CODE>
MAINNET_0_URL='https://api.s0.t.hmny.io'

GAS_LIMIT=3321900
GAS_PRICE=1000000000
```

### Configuring Truffle

In the project root directory, there is a file `truffle-config.js` and copy paste the following configuration.

```javascript
require("dotenv").config();
const { TruffleProvider } = require("@harmony-js/core");

//Local
const local_mnemonic = process.env.LOCAL_MNEMONIC;
const local_private_key = process.env.LOCAL_PRIVATE_KEY;
const local_url = process.env.LOCAL_0_URL;

//Testnet
const testnet_mnemonic = process.env.TESTNET_MNEMONIC;
const testnet_private_key = process.env.TESTNET_PRIVATE_KEY;
const testnet_url = process.env.TESTNET_0_URL;

//Mainnet
const mainnet_mnemonic = process.env.MAINNET_MNEMONIC;
const mainnet_private_key = process.env.MAINNET_PRIVATE_KEY;
const mainnet_url = process.env.MAINNET_0_URL;

//GAS - Currently using same GAS accross all environments
gasLimit = process.env.GAS_LIMIT;
gasPrice = process.env.GAS_PRICE;

module.exports = {
  networks: {
    local: {
      network_id: "2", // Any network (default: none)
      provider: () => {
        const truffleProvider = new TruffleProvider(
          local_url,
          { memonic: local_mnemonic },
          { shardID: 0, chainId: 2 },
          { gasLimit: gasLimit, gasPrice: gasPrice }
        );
        const newAcc = truffleProvider.addByPrivateKey(local_private_key);
        truffleProvider.setSigner(newAcc);
        return truffleProvider;
      },
    },
    testnet: {
      network_id: "2", // Any network (default: none)
      provider: () => {
        const truffleProvider = new TruffleProvider(
          testnet_url,
          { memonic: testnet_mnemonic },
          { shardID: 0, chainId: 2 },
          { gasLimit: gasLimit, gasPrice: gasPrice }
        );
        const newAcc = truffleProvider.addByPrivateKey(testnet_private_key);
        truffleProvider.setSigner(newAcc);
        return truffleProvider;
      },
    },
    mainnet0: {
      network_id: "1", // Any network (default: none)
      provider: () => {
        const truffleProvider = new TruffleProvider(
          mainnet_url,
          { memonic: mainnet_mnemonic },
          { shardID: 0, chainId: 1 },
          { gasLimit: gasLimit, gasPrice: gasPrice }
        );
        const newAcc = truffleProvider.addByPrivateKey(mainnet_private_key);
        truffleProvider.setSigner(newAcc);
        return truffleProvider;
      },
    },
  }
};

```
