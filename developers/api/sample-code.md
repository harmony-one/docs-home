---
description: This page provides examples of using the RPC methods in this section.
---

# Sample Code

## Setting Up an Account

```javascript
const mnes = 'urge clog right example dish drill card maximum mix bachelor section select';
const password = 'some phrase';
const added_mnemonic = harmony.wallet.addByMnemonic(mnes, 0);
await harmony.wallet.encryptAccount(added_mnemonic.address, password);
```

## Creating a Transaction Object

```javascript
const txn_object = {
    nonce: id,
    gasPrice: new Unit(0).asWei().toWei(),
    gasLimit: new Unit(21000).asWei().toWei(),
    shardID: 0,
    to: getAddress('one129r9pj3sk0re76f7zs3qz92rggmdgjhtwge62k').checksum,
    value: new Unit('1000000000000000000').asWei().toWei(),
    data: '0x',
};
```

## hmy\_sendRawTransaction

```javascript
const txn = harmony.transactions.newTx(txn_object);
const signed = await harmony.wallet.signTransaction(txn, harmony.wallet.signer, password);
console.log(signed.getRawTransaction());
const [Transaction, hash] = await signed.sendTransaction();
const confirmed = await Transaction.confirm(hash);
console.log('Transaction Receipt', confirmed.receipt);
if (confirmed.isConfirmed()) {
  console.log('transaction did go through');
}
```
