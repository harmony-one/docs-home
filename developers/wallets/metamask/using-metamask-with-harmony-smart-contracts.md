# Using Metamask with Harmony Smart Contracts

{% hint style="info" %}
For instructions on how to install and setup Metamask to work with Harmony blockchain please click [here](../../../network/wallets/browser-extensions-wallets/metamask-wallet/).
{% endhint %}

## Project Setup

The completed code can be found [here](https://github.com/rachit2501/Smart-Contract-Demo/tree/master/MetaMask).

For reference, the smart contract code will look as follows:

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

For setting up your own project just replace the code in `userWallet.js` in One Wallet guide with the following.

```javascript
import detectEthereumProvider from "@metamask/detect-provider";

let ethAddress;
let isAuthorised = false;

const handleAccountsChanged = (accounts) => {
  if (accounts.length === 0) {
    console.error("Not found accounts");
  } else {
    ethAddress = accounts[0];

    console.log("Your address: ", ethAddress);
  }
};

export const signInMetamask = async () => {
  const provider = await detectEthereumProvider();

  // @ts-ignore
  if (provider !== window.ethereum) {
    console.error("Do you have multiple wallets installed?");
  }

  if (!provider) {
    console.error("Metamask not found");
    return;
  }

  // MetaMask events
  provider.on("accountsChanged", handleAccountsChanged);

  provider.on("disconnect", () => {
    console.log("disconnect");
    isAuthorised = false;
  });

  provider.on("chainIdChanged", (chainId) =>
    console.log("chainIdChanged", chainId)
  );

  provider
    .request({ method: "eth_requestAccounts" })
    .then(async (params) => {
      handleAccountsChanged(params);
      isAuthorised = true;
    })
    .catch((err) => {
      isAuthorised = false;

      if (err.code === 4001) {
        console.error("Please connect to MetaMask.");
      } else {
        console.error(err);
      }
    });
};

```

This will connect your metamask.

## Making Calls

Setup your contract object. In`init.js`:

```javascript
import { signInMetamask } from "./walletStore";
import Web3 from "web3";
import fs from "fs";
let but = document.getElementById("inputtButton");

let web3;
let contract;

async function setupContract() {
  let contractFile = fs.readFileSync("../build/contracts/Counter.json", {
    encoding: "UTF-8",
  });
  contractFile = JSON.parse(contractFile);
  const abi = contractFile.abi;
  const contractAddress = contractFile.networks["2"].address;
  await signInMetamask();
  web3 = new Web3(window.web3.currentProvider);

  const contractInstance = new web3.eth.Contract(abi, contractAddress);
  contract = contractInstance;
}

```

#### Making a Payable Contract Call

```javascript

async function demoInteraction() {
  await setupContract();
  const accounts = await web3.eth.getAccounts();
  console.log(accounts);
  const increment = await contract.methods
    .addMoney()
    .send({ from: accounts[0], value: web3.utils.wei });
  console.log(increment);
}
```

#### Making a Read-Only Call

```javascript
await setupContract();
const value = await contract.methods.getMoneyStored().call();
```

## Congratulations

You just completed the tutorial to interact with smart contract using metamask and web3 on Harmony Network!
