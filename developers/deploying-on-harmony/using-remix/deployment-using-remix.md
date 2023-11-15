---
description: >-
  This guide shows instructions on how to deploy smart contracts using Harmony
  remix ide.
---

# Harmony Remix

### Remix IDE Harmony

Open [Harmony Remix IDE](https://ide.harmony.one/#optimize=false\&evmVersion=null) in your browser.

### Writing your Smart Contract

On opening the IDE, in the left panel, click the "+" icon to create a new solidity file:

<div align="left">

<img src="../../../.gitbook/assets/Screenshot from 2020-11-02 002600.png" alt="">

</div>

Now click on the new file in the navigation panel, if not opened already. Now start writing your code in the window opened on the right hand side. For this demo we are going to use a simple counter smart contract:

![](<../../../.gitbook/assets/Screenshot from 2020-11-02 002550.png>)

Following is the code used in the demo image above:

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

### Compiling

In the left navigation bar select "Solidity Compiler". In the new window choose the solidity version and modify other settings if required. Finally click on the Compile button to compile your solidity code:

![](<../../../.gitbook/assets/Screenshot from 2020-11-02 002639.png>)

### Deployment

After successful compilation, go the navigation panel once again, and click on the "Harmony" button. Now in the new panel, select the network to deploy on, and choose and connect to your desired wallet. For this demo we are using Math Wallet. Now click on "Deploy" to deploy your smart contract to Harmony Network:

![](<../../../.gitbook/assets/Screenshot from 2020-11-02 002905.png>)

### Congratulations

You have now successfully deployed your smart contract on harmony network!
