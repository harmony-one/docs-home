# Using Band Oracle

The repo [https://github.com/harmony-one/band\_oracle](https://github.com/harmony-one/band\_oracle) contains examples on how to fetch price feeds using band oracle.

There are two scenarios:

* Fetching price feed in your javascript application code
* Fetching price feed in your smart contract

### Requesting data using BandChain.js library

[https://github.com/harmony-one/band\_oracle/blob/main/main.js](https://github.com/harmony-one/band\_oracle/blob/main/main.js)

```
git clone https://github.com/harmony-one/band_oracle
cd band_oracle

yarn
node main.js
```

### Using BandChain data in EVM Smart Contract in Harmony

[https://github.com/harmony-one/band\_oracle](https://github.com/harmony-one/band\_oracle)

```
git clone https://github.com/harmony-one/band_oracle
cd band_oracle

yarn
export PRIVATE_KEY=place your private key here
yarn hardhat run ./scripts/deploy.js
```

Contract's been deployed and you can call `getPrice` or `getMultiPrices` to get actual prices. More details with code snippets are in [https://docs.harmony.one/home/developers/tools/oracle-band-protocol](https://docs.harmony.one/home/developers/tools/oracle-band-protocol)

{% hint style="info" %}
Band’s StdReference contract for testnet **0xE740092E081CA7491A46C8Aa0175446e962e2A08**

Mainnet contract is coming soon...
{% endhint %}
