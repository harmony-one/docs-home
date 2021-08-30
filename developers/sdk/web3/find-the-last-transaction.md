# Find the last transaction

### Introduction <a id="introduction"></a>

This guide walks through the process of using [web3.js](https://web3js.readthedocs.io/) to get last block and get last transaction.

For this example, we will use Node.js and straightforward JavaScript code.

{% hint style="info" %}
This example assumes that you have configured Web3 as described in the previous section.
{% endhint %}

#### Get Block Number

```javascript
const lastBlockNumber = await web3.eth.getBlockNumber();
console.log('Last block number: ', lastBlockNumber);

let block = await web3.eth.getBlock(lastBlockNumber);

console.log('Last block hash: ', block.hash);
console.log('Last block transactions: ', block.transactions);
```

#### Get Last Transaction

```javascript
block = await web3.eth.getBlock(blockNumber);

const lastTransaction = block.transactions[block.transactions.length - 1];
console.log('Last transaction hash: ', lastTransaction);

const transaction = await web3.eth.getTransaction(lastTransaction);
console.log('Last transaction: ', JSON.stringify(transaction));
```

Code samples can be found [here.](https://github.com/harmony-one/ethhmy-bridge.sdk/blob/web3-hmy/examples/web3-hmy/get-block-transactions.js)

