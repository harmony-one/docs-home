---
description: A cradle to grave transaction example
---

# Sample nodejs CLI Application

Let's build a small CLI application in nodejs v11.11.0 that creates keys and posts a transaction to the Harmony blockchain. We'll built it up piece by piece and post the full copy pastable script at the end of this tutorial. Moving forward, first let's take care of our dependencies: 

```bash
yarn add @harmony-js/core@next inquirer chalk
```

And let's make sure our local harmony network is on by running `./test/debug.sh` inside of our cloned Harmony repo. 

Now our imported dependencies that we'll use:

```javascript
const { Harmony } = require('@harmony-js/core');
const { ChainID, ChainType, Unit } = require('@harmony-js/utils');
const inquirer = require('inquirer');
const chalk = require('chalk');
const { getAddress } = require('@harmony-js/crypto')
```

We'll use a top level anonymous async function as a modern `IIFE`

```javascript
(async () => {
  console.log(chalk.yellow(`Make sure you have your Harmony local network running!\n`));
  /* Now lets use the abstractions provided by the SDK */
  const harmony = new Harmony('ws://localhost:9800', {
    chainUrl: 'ws://localhost:9800',
    chainId: ChainID.Default,
    chainType: ChainType.Harmony,
  });
  const mnes = 'urge clog right example dish drill card maximum mix bachelor section select';
  console.log(chalk.yellow(`We will make our own Private keys\n`));
  const { password } = await inquirer.prompt([
    { type: 'input', name: 'password', message: 'Password' },
  ]);

  const added_mnemonic = harmony.wallet.addByMnemonic(mnes, 0);
  await harmony.wallet.encryptAccount(added_mnemonic.address, password);
  const addr = getAddress(harmony.wallet.signer.address).bech32;

})();
```

Here we use the `Harmony` object provided by our sdk and connect to the locally running Harmony RPC via WebSockets and we make an account with its own private keys. We can see our Harmony wallet address in the `addr` variable. 

Now let's prompt the user to fund their account

```javascript
  console.log(
    chalk.blue(
      `Look at "./bin/wallet -p local balances" and then fund to your address (${addr}) like so:\n`
    )
  );
  console.log(`./bin/wallet -p local transfer --from SOME_FUNDED_ACCOUNT --to ${addr} --amount 50`);
  const { to } = await inquirer.prompt([
    {
      type: 'input',
      name: 'to',
      message: 'Now who are we sending coin to, after checking with ./bin/wallet -p local balances',
    },
  ]);

```

Recall you can see all the local balances with the `./bin/wallet` from within the Harmony repo and find an account to transfer from: 

```bash
./bin/wallet -p local balances
Using local profile for wallet
Account 0:
    Address: one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7
    Balance in Shard 0:  1855.657142857, nonce: 0
    Balance in Shard 1:  0.0000, nonce: 0
Account 1:
    Address: one129r9pj3sk0re76f7zs3qz92rggmdgjhtwge62k
    Balance in Shard 0:  0.0000, nonce: 0
    Balance in Shard 1:  1853.6, nonce: 0
    ....
```

Now let's make a transaction, sign it and send it off to the blockchain

```javascript
  const txn_object = {
    nonce: 0,
    gasPrice: new Unit(10).asWei().toWei(),
    gasLimit: new Unit(21000).asWei().toWei(),
    shardID: 0,
    to: getAddress(to).checksum,
    value: new Unit('1000000000000000000').asWei().toWei(),
    data: '0x',
  };
  const txn = harmony.transactions.newTx(txn_object);
  const signed = await harmony.wallet.signTransaction(txn, harmony.wallet.signer, password);
  const [Transaction, hash] = await signed.sendTransaction();
  console.log(`This hash is our receipt of the transaction ${chalk.blue(hash)}`);
  const confirmed = await Transaction.confirm(hash);
  if (confirmed.isConfirmed()) {
    console.log('transaction did go through');
  }

```

And when `confirm` resolves and we check the result of `isConfirmed`, then we know our transaction is on the blockchain. 



Here is the full copy-pastable script: 

```javascript
const { Harmony } = require('@harmony-js/core');
const { ChainID, ChainType, Unit } = require('@harmony-js/utils');
const inquirer = require('inquirer');
const chalk = require('chalk');
const { getAddress } = require('@harmony-js/crypto');

(async () => {
  console.log(chalk.yellow(`Make sure you have your Harmony local network running!\n`));
  /* Now lets use the abstractions provided by the SDK */
  const harmony = new Harmony('ws://localhost:9800', {
    chainUrl: 'ws://localhost:9800',
    chainId: ChainID.Default,
    chainType: ChainType.Harmony,
  });

  // Note: mnes should be 75 length long
  const mnes = 'urge clog right example dish drill card maximum mix bachelor section select';
  console.log(chalk.yellow(`We will make our own Private keys\n`));
  const { password } = await inquirer.prompt([
    { type: 'input', name: 'password', message: 'Password' },
  ]);

  const added_mnemonic = harmony.wallet.addByMnemonic(mnes, 0);
  await harmony.wallet.encryptAccount(added_mnemonic.address, password);
  const addr = getAddress(harmony.wallet.signer.address).bech32;

  console.log(
    chalk.blue(
      `Look at "./bin/wallet -p local balances" and then fund to your address (${addr}) like so:\n`
    )
  );

  console.log(`./bin/wallet -p local transfer --from SOME_FUNDED_ACCOUNT --to ${addr} --amount 50`);

  const { to } = await inquirer.prompt([
    {
      type: 'input',
      name: 'to',
      message: 'Now who are we sending coin to, after checking with ./bin/wallet -p local balances',
    },
  ]);

  const txn_object = {
    nonce: 0,
    gasPrice: new Unit(10).asWei().toWei(),
    gasLimit: new Unit(21000).asWei().toWei(),
    shardID: 0,
    to: getAddress(to).checksum,
    value: new Unit('1000000000000000000').asWei().toWei(),
    data: '0x',
  };

  const txn = harmony.transactions.newTx(txn_object);
  const signed = await harmony.wallet.signTransaction(txn, harmony.wallet.signer, password);

  const [Transaction, hash] = await signed.sendTransaction();
  console.log(`This hash is our receipt of the transaction ${chalk.blue(hash)}`);

  const confirmed = await Transaction.confirm(hash);
  if (confirmed.isConfirmed()) {
    console.log('transaction did go through');
  }
})();

```

