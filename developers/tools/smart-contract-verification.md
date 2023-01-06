# Smart Contract Verification

A quick guide on how to verify your contracts on Harmony.

[https://explorer.harmony.one/verifycontract](https://explorer.harmony.one/verifycontract)

Right now, we support verification only for one single solidity file - therefore, before deployment and verification, you will need to flatten all solidity sources to one file.

## 1. Flatten your solidity files (only for multiple files)

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

![](<../../.gitbook/assets/verify\_contract (2) (4) (5) (2) (1) (1) (1) (2) (1) (2).png>)

Important to use correct params (the same like on deploy):

* Contract address
* Contract name
* Compiler version
* Optimizer
* Chain Type (mainnet or testnet)
* Sources
* Imported libs

Then click **Submit** button

If all parameters are correct - you should to see `Success` message, or `Error` if bytecodes don't equal

On Success case - you contract will verify and you will see all contract details on contract explorer page

![](<../../.gitbook/assets/untitled-1 (2) (4) (5) (5) (3) (1) (1) (1) (2) (1) (4).png>)

## 4. Verify contract with constructor arguments (for contracts that were created with constructor parameters)

[https://docs.soliditylang.org/en/develop/abi-spec.html](https://docs.soliditylang.org/en/develop/abi-spec.html)

To get ABI-encoded constructor arguments you can ue this service: [https://abi.hashex.org](https://abi.hashex.org)

Example for Harmony Remix:

1 - click ABI to copy it ![image](https://user-images.githubusercontent.com/57394565/126634721-b3762b14-9e43-4313-b6f6-5e2c5126e1c2.png)

2 - paste ABI to [https://abi.hashex.org](https://abi.hashex.org) form and click parse ![image](https://user-images.githubusercontent.com/57394565/126634847-5f2917ef-ee72-41d6-b246-401b1b9b5b0d.png)

3 - paste your constuctor arguments and click Copy ![image](https://user-images.githubusercontent.com/57394565/126634955-2b458846-540e-4d56-94a1-ce9c26cf3a03.png)

4 - paste encoded constructor arguments to verify form field ![image](https://user-images.githubusercontent.com/57394565/126635142-570cd58e-0f44-4af6-98f3-0b9b8d6095d9.png)
