# Smart Contract Verification

[https://explorer.harmony.one/verifycontract](https://explorer.harmony.one/verifycontract)

Right now, we support verification only for one single solidity file - therefore, before deployment and verification, you will need to flatten all solidity sources to one file.

## 1. Flatten your Solidity Files

To flatten your solidity files we recommended to use [Truffle Flattener lib](https://www.npmjs.com/package/truffle-flattener).

```javascript
npm install truffle-flattener -g
truffle-flattener <solidity-files>
```

Or you can use any other flattener lib.

## 2. Deploy Contract to Harmony

To easy the verification we recommend the contract deployment using [Harmony Remix](using-remix/deployment-using-remix.md).

## 3. Verify Contract

You can verify your contract here: [https://explorer.harmony.one/verifycontract](https://explorer.harmony.one/verifycontract)

![Verify Contract](../../.gitbook/assets/verify_contract%20%282%29%20%284%29%20%285%29%20%282%29%20%283%29.png)

It is important to use the correct parameters \(same as on deployment\):

* Contract address
* Contract name
* Compiler version
* Optimizer
* Chain Type \(mainnet or testnet\)
* Sources
* Imported libs

Then click on **Sumbit** button. If all params was correct - you should to see Success message, or Error if bytecodes are not equal. On Success case - you contract will verify and you will see all contract details on contract explorer page.

![Contract Verification](../../.gitbook/assets/untitled-1%20%282%29%20%284%29%20%285%29%20%285%29.png)

