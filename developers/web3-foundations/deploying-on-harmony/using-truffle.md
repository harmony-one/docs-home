# Using Truffle

1\. Install truffle (preferably v5.3.0+, sometimes with v5.1.33, `@truffle/hdwallet-provider` does not work)&#x20;

```
npm install -g truffle
```

2\. Create a metacoin project, unbox metacoin truffle box, and install `@truffle/hdwallet-provider`

```
mkdir metacoin
truffle unbox metacoin
npm install --save-dev @truffle/hdwallet-provider
```

3\. Modify `truffle-config.js` to add Harmony networks. Make sure to add your mnemonic or private key.

```
const HDWalletProvider = require('@truffle/hdwallet-provider');
const mnemonic = '<ADD-YOUR-MNEMONIC-HERE>';
const privateKeyTest = '<ADD-YOUR-PRIVATE-KEY-HERE>';

module.exports = {
  networks: {
    testnet: {
      provider: () => {
        return new HDWalletProvider({
          mnemonic,
          providerOrUrl: 'https://api.s0.b.hmny.io', // https://api.s0.t.hmny.io for mainnet
          derivationPath: `m/44'/1023'/0'/0/`
        });
      },
      network_id: 1666700000, // 1666600000 for mainnet
    },
    testnetHar: {
      provider: () => {
        if (!privateKeyTest.trim()) {
          throw new Error(
            'Please enter a private key with funds, you can use the default one'
          );
        }
        return new HDWalletProvider({
          privateKeys: [privateKeyTest],
          providerOrUrl: 'https://api.s0.b.hmny.io',
        });
      },
      network_id: 1666700000,
    },
  },
};
```

4\. Compile and deploy

```
truffle compile
truffle deploy --network testnet
```
