---
description: >-
  This page explains how to get the latest price of ONE and other HRC20 assets
  inside smart contracts, using the Chainlink Price Feed on the Harmony testnet.
---

# Chainlink

## The Price Feed Contracts

```text
DAI-USD: 0x1FA508EB3Ac431f3a9e3958f2623358e07D50fe0
ETH-USD: 0x4f11696cE92D78165E1F8A9a4192444087a45b64
DSLA-USD: 0x5f0423B1a6935dc5596e7A24d98532b67A0AeFd8
USDC-USD: 0x6F2bD4158F771E120d3692C45Eb482C16f067dec
SUSHI-USD: 0x90142a6930ecF80F1d14943224C56CFe0CD0d347
USDT-USD: 0x9A37E1abFC430B9f5E204CA9294809c1AF37F697
WBTC-USD: 0xEF637736B220a58C661bfF4b71e03ca898DCC0Bd
BUSD-USD: 0xa0ABAcC3162430b67Aa6C135dfAA08E117A38bF0
ONE-USD: 0xcEe686F89bc0dABAd95AEAAC980aE1d97A075FAD
LINK-USD: 0xcd11Ac8C18f3423c7a9C9d5784B580079A75E69a
```

## Solidity

To consume price data, your smart contract should reference [`AggregatorV3Interface`](https://github.com/smartcontractkit/chainlink/blob/master/contracts/src/v0.6/interfaces/AggregatorV3Interface.sol), which defines the external functions implemented by Price Feeds.

```text
pragma solidity ^0.6.7;

import "@chainlink/contracts/src/v0.6/interfaces/AggregatorV3Interface.sol";

contract PriceConsumerV3 {

    AggregatorV3Interface internal priceFeed;

    /**
     * Network: Kovan
     * Aggregator: ONE/USD
     * Address: 0xcEe686F89bc0dABAd95AEAAC980aE1d97A075FAD
     */
    constructor() public {
        priceFeed = AggregatorV3Interface(0xcEe686F89bc0dABAd95AEAAC980aE1d97A075FAD);
    }

    /**
     * Returns the latest price
     */
    function getThePrice() public view returns (int) {
        (
            uint80 roundID, 
            int price,
            uint startedAt,
            uint timeStamp,
            uint80 answeredInRound
        ) = priceFeed.latestRoundData();
        return price;
    }
}

```

## Javascript

The `latestRoundData` function returns five values representing information about the latest price data. See [Price Feeds API Reference](https://docs.chain.link/docs/price-feeds-api-reference/) for more details.

```text
const web3 = new Web3("https://api.s0.b.hmny.io");
const aggregatorV3InterfaceABI = [{"inputs":[],"name":"decimals","outputs":[{"internalType":"uint8","name":"","type":"uint8"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"description","outputs":[{"internalType":"string","name":"","type":"string"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint80","name":"_roundId","type":"uint80"}],"name":"getRoundData","outputs":[{"internalType":"uint80","name":"roundId","type":"uint80"},{"internalType":"int256","name":"answer","type":"int256"},{"internalType":"uint256","name":"startedAt","type":"uint256"},{"internalType":"uint256","name":"updatedAt","type":"uint256"},{"internalType":"uint80","name":"answeredInRound","type":"uint80"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"latestRoundData","outputs":[{"internalType":"uint80","name":"roundId","type":"uint80"},{"internalType":"int256","name":"answer","type":"int256"},{"internalType":"uint256","name":"startedAt","type":"uint256"},{"internalType":"uint256","name":"updatedAt","type":"uint256"},{"internalType":"uint80","name":"answeredInRound","type":"uint80"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"version","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"}];
const addr = "0xcEe686F89bc0dABAd95AEAAC980aE1d97A075FAD";
const priceFeed = new web3.eth.Contract(aggregatorV3InterfaceABI, addr);
priceFeed.methods.latestRoundData().call()
    .then((roundData) => {
        // Do something with roundData
        console.log("Latest Round Data", roundData)
    });
```

Sample output when you run the above code:

```text
Latest Round Data Result {
  '0': '18446744073709552763',
  '1': '11429419',
  '2': '1629106535',
  '3': '1629106535',
  '4': '18446744073709552763',
  roundId: '18446744073709552763',
  answer: '11429419',
  startedAt: '1629106535',
  updatedAt: '1629106535',
  answeredInRound: '18446744073709552763'
}
```

## Python

```text
from web3 import Web3
web3 = Web3(Web3.HTTPProvider('https://api.s0.b.hmny.io'))
abi = '[{"inputs":[],"name":"decimals","outputs":[{"internalType":"uint8","name":"","type":"uint8"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"description","outputs":[{"internalType":"string","name":"","type":"string"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint80","name":"_roundId","type":"uint80"}],"name":"getRoundData","outputs":[{"internalType":"uint80","name":"roundId","type":"uint80"},{"internalType":"int256","name":"answer","type":"int256"},{"internalType":"uint256","name":"startedAt","type":"uint256"},{"internalType":"uint256","name":"updatedAt","type":"uint256"},{"internalType":"uint80","name":"answeredInRound","type":"uint80"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"latestRoundData","outputs":[{"internalType":"uint80","name":"roundId","type":"uint80"},{"internalType":"int256","name":"answer","type":"int256"},{"internalType":"uint256","name":"startedAt","type":"uint256"},{"internalType":"uint256","name":"updatedAt","type":"uint256"},{"internalType":"uint80","name":"answeredInRound","type":"uint80"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"version","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"}]'
addr = '0xcEe686F89bc0dABAd95AEAAC980aE1d97A075FAD'
contract = web3.eth.contract(address=addr, abi=abi)
latestData = contract.functions.latestRoundData().call()
print(latestData)
```

  
  


