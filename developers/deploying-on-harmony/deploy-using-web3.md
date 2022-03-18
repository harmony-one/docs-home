# Using Web3

This guide walks you through the process of using the Solidity compiler and [web3.js](https://web3js.readthedocs.io) to deploy and interact with a Solidity-based smart contract on Harmony. Given Harmony's Ethereum compatibility features, the web3.js library can be used directly with a Harmony node.

Completed code can be found [here.](https://github.com/harmony-one/Smart-Contract-Demo/tree/master/Web3-deployment)

### Installation

```
npm i dotenv
npm i solc
npm i @truffle/hdwallet-provider web3
```

#### Create a file Counter.sol in root.

```
pragma solidity >=0.4.22;

contract Counter {
    uint256 private count = 0;
    uint256 moneyStored = 0;

    function incrementCounter() public {
        count += 1;
    }
    function decrementCounter() public {
        count -= 1;
    }

    function addMoney() payable public {
        moneyStored += msg.value;
    }

    function getCount() public view returns (uint256) {
        return count;
    }

    function getMoneyStored() public view returns (uint256){
        return moneyStored;
    }
}
```

#### Create `compile.js`

The only purpose of the _`compile.js`_ file, is to use the Solidity compiler to output the bytecode and interface of our contract.

```
const path = require("path");
const fs = require("fs");
const solc = require("solc");

// Compile contract
const contractPath = path.resolve(__dirname, "Counter.sol");
const source = fs.readFileSync(contractPath, "utf8");
const input = {
  language: "Solidity",
  sources: {
    "Counter.sol": {
      content: source,
    },
  },
  settings: {
    outputSelection: {
      "*": {
        "*": ["*"],
      },
    },
  },
};
const tempFile = JSON.parse(solc.compile(JSON.stringify(input)));
const contractFile = tempFile.contracts["Counter.sol"]["Counter"];
module.exports = contractFile;

```

#### Create `Deploy.js`

```
require("dotenv").config();
const Web3 = require("web3");
const contractFile = require("./compile");
const HDWalletProvider = require("@truffle/hdwallet-provider");

const bytecode = contractFile.evm.bytecode.object;
const abi = contractFile.abi;

const provider = new HDWalletProvider(
  process.env.mneumonic,
  process.env.rpcEndpoint
);

const web3 = new Web3(provider);

const deploy = async () => {
  console.log("Deploying....");
  I;
  const accounts = await web3.eth.getAccounts();
  const result = await new web3.eth.Contract(abi)
    .deploy({ data: "0x" + bytecode })
    .send({ gas: "3000000", from: accounts[0] });

  console.log("Contract deployed to", result.options.address);
  process.exit();
};

deploy();

```

#### Finally&#x20;

```
node deploy.js
```

### Congratulations

You just deployed your first smart contract on Harmony using web3.js.
