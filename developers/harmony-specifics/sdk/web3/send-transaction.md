# Using Web3.js to Send Transactions on Harmony

### Introduction <a href="introduction" id="introduction"></a>

This guide walks through the process of using [web3.js](https://web3js.readthedocs.io) to manually sign and send a transaction to a Harmony network. For this example, we will use Node.js and straightforward JavaScript code.

For this guide we will use Harmony Testnet Network.

### Install Dependencies

Next, we can create a directory to store all our relevant files by running:

```
mkdir transaction && cd transaction/
```

And create a simple package.json file:

```
npm init --yes
```

With the package.json file created, we can then install the web3.js package by executing:

```
npm install web3
npm install 'bn.js'
```

{% hint style="info" %}
We recommended to use[ bn.js](https://github.com/indutny/bn.js/) for format values
{% endhint %}

To verify the installed version of web3.js, you can use the `ls` command:

```
npm ls web3
```

As of the writing of this guide, the version used was 1.3.0.

### Sending Transaction

For our example, we only need a single JavaScript file (arbitrarily named _transaction.js_, which you can find [here](https://github.com/harmony-one/ethhmy-bridge.sdk/blob/web3-hmy/examples/web3-hmy/send-transaction.js)) to create and send the transaction, which we will run using the `node` command in the terminal. The script will transfer 1 ONE from the genesis account to another address. For simplicity, the file is divided into three sections: variable definition, create transaction, and deploy transaction.

We need to set a couple of values in the variable definitions:

1. Create our Web3 constructor (`Web3`).
2. Define the `HMY_PRIVATE_KEY` variable as the private key of your ONE wallet, what is used to sign the transactions.
3. Create a local Web3 instance and set the provider to connect to Testnet Harmony network.

#### Setup Account

```javascript
const Web3 = require('web3');
const BN = require('bn.js');

HMY_PRIVATE_KEY = 'YOUR_PRIVATE_KEY';
HMY_TESTNET_RPC_URL = 'https://api.s0.b.hmny.io';

const web3 = new Web3(HMY_TESTNET_RPC_URL);

let hmyMasterAccount = web3.eth.accounts.privateKeyToAccount(HMY_PRIVATE_KEY);
web3.eth.accounts.wallet.add(hmyMasterAccount);
web3.eth.defaultAccount = hmyMasterAccount.address

const myAddress = web3.eth.defaultAccount;
console.log('My address: ', myAddress);
```

#### Check Account Balance

```javascript
const balance = await web3.eth.getBalance(myAddress);
console.log('My balance: ', balance / 1e18);
```

#### Create new account on which we will send tokens

```javascript
const newAccount = web3.eth.accounts.create();
console.log('New account created: ', newAccount.address);
```

#### Sending a Transaction

```javascript
const gasPrice = new BN(await web3.eth.getGasPrice()).mul(new BN(1));
const gasLimit = 6721900;

const value = 1 * 1e18; // 1 ONE

const from = web3.eth.defaultAccount;
const to = newAccount.address; // account was created on prev step

const result = await web3.eth
      .sendTransaction({ from, to, value, gasPrice, gasLimit })
      .on('error', console.error);
      
console.log(`Send tx: ${result.transactionHash} result: `, result.status);

const newAddrBalance = await web3.eth.getBalance(newAccount.address);
console.log('New account balance: ', newAddrBalance / 1e18);
```

Full code samples can be found [here.](https://github.com/harmony-one/ethhmy-bridge.sdk/blob/web3-hmy/examples/web3-hmy/send-transaction.js)
