# Ethereum Remix

Go to [https://remix.ethereum.org/](https://remix.ethereum.org/)

### Writing your smart contract

![1. Create a "New File" under contracts with name Counter.sol](<../../../../.gitbook/assets/Screen Shot 2021-06-12 at 5.24.11 PM.png>)

Copy and paste the code below to Counter.sol file

```
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

### Compiling

![2. Compile Counter.sol](../../../../.gitbook/assets/compile.png)

### Deploying

If you want to deploy the contract to a live network like Harmony Testnet or Mainnet, configure your metamask by adding the required Harmony networks using this [guide](https://docs.harmony.one/home/network/wallets/browser-extensions-wallets/metamask-wallet).

![3. Deploy the compiler contract. Select Injected Web3 for deploying to live network like Harmony testnet.](../../../../.gitbook/assets/deploy.png)

![4. Confirm the deploy transaction in metamask and you can find the deployed contract address.](../../../../.gitbook/assets/deployed.png)





###
