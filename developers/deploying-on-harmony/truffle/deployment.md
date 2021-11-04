---
description: >-
  This section covers writing a custom smart contract and deploying it on
  Harmony Testnet.
---

# Compile & Deploy

### Writing our first Counter Smart Contract

In the contracts folder create a new file `Counter.sol` and add the following code block to it:

```javascript
pragma solidity >=0.4.22 <0.8.0;

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

In the migrations folder create another new file called `2_Counter.js` and add the following code block:

```javascript
const Migrations = artifacts.require("Counter");

module.exports = function (deployer) {
  deployer.deploy(Migrations);
};
```

### Checking the Solidity Smart Contract

```
truffle compile
```

If all was done correctly you should see something like this:

```
Compiling your contracts...
===========================
> Compiling ./contracts/Counter.sol
> Compiling ./contracts/Migrations.sol
> Compilation warnings encountered:

    /home/rachit/Projects/demo/contracts/Counter.sol: Warning: SPDX license identifier not provided in source file. Before publishing, consider adding a comment containing "SPDX-License-Identifier: <SPDX-License>" to each source file. Use "SPDX-License-Identifier: UNLICENSED" for non-open-source code. Please see https://spdx.org for more information.

> Artifacts written to /home/rachit/Projects/demo/build/contracts
> Compiled successfully using:
   - solc: 0.7.0+commit.9e61f92b.Emscripten.clang
```

### Deployment

```
truffle migrate  --network testnet --reset
```
