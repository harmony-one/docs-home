# Smart Contract Verification

A quick guide on how to verify your contacts on Harmony.

[https://explorer.harmony.one/verifycontract](https://explorer.harmony.one/verifycontract)

Right now, we support verification only for one single solidity file - therefore, before deployment and verification, you will need to flatten all solidity sources to one file.

## 1. Flatten your solidity files

To flatten your solidity files we recommended to use [https://www.npmjs.com/package/truffle-flattener](https://www.npmjs.com/package/truffle-flattener)

```jsx
npm install truffle-flattener -g

truffle-flattener <solidity-files>
```

Or you can use any other flattener lib

## 2. Deploy contract to Harmony

To more easy verification we recommend to deploy contract with Harmony Remix [https://docs.harmony.one/home/developers/deploying-on-harmony/using-remix/deployment-using-remix](https://docs.harmony.one/home/developers/deploying-on-harmony/using-remix/deployment-using-remix)

## 3. Verify contract

You can verify your contract here [https://explorer.harmony.one/verifycontract](https://explorer.harmony.one/verifycontract)

![](../../.gitbook/assets/verify_contract%20%281%29.png)

Important to use correct params \(the same like on deploy\):

* Contract address
* Contract name
* Compiler version
* Optimizer
* Chain Type \(mainnet or testnet\)
* Sources
* Imported libs

Then click **Submit** button

If all parameters are correct - you should to see `Success` message, or `Error` if bytecodes don't equal

On Success case - you contract will verify and you will see all contract details on contract explorer page

![](../../.gitbook/assets/untitled-1%20%281%29.png)

