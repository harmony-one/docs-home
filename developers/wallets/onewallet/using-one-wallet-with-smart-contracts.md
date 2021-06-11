# Using One Wallet with Smart Contracts

Add the following lines to your `src/init.js`

```text
import initializeContract from './contract';
import userWallet from './userWallet';

let but = document.getElementById("inputtButton");

but.addEventListener("click",initWallet);

async function initWallet(){
    const wallet = new userWallet();
    await wallet.signin();
    const contract = await initializeContract();
    console.log(contract)
    const result = await contract.methods.getCount().call()
    console.log(result.toString())
}
```

In you `src/hmy.js` file, add the following lines of code

```text
const { Harmony } = require('@harmony-js/core');
const { ChainType } = require('@harmony-js/utils');

export default new Harmony(
  // let's assume we deploy smart contract to this end-point URL
  'https://api.s0.b.hmny.io',
  {
    chainType: ChainType.Harmony,
    chainId: 2,
  },
);
```

Now add the following lines of code to `src/contract.js`

```text
import hmy from './hmy';
import fs from 'fs';

const initializeContract = async (wallet)=>{
    let contract = fs.readFileSync("../build/contracts/Counter.json" , { encoding: "UTF-8" });
    contract = JSON.parse(contract)
    const abi = contract.abi;
    const contractAddress = contract.networks['2'].address;
    const contractInstance = hmy.contracts.createContract(abi,contractAddress);
    return contractInstance    
}

export default initializeContract;
```

To sign the transactions when calling send method on a smart contract, add the following lines to wallet class in `src/userWallet.js`

```text
      signTransaction(txn) {
        if (this.isOneWallet) {
          return this.onewallet.signTransaction(txn);
        }
      }

      attachToContract(contract) {
        if(this.onewallet){
          contract.wallet.signTransaction = async (tx)=>{
            tx.from = this.address;
            const signTx = await this.signTransaction(tx);
            console.log(signTx);
            return signTx;
          }
        }
        return contract
      }
```

> We assume that you are using the same setup structure throughout the documentation. If not, change the path of `Counter.json` to your desired location.

### That's It !!

Now call "view" methods on smart contracts like this:

```text
  const value = await contract.methods.getMoneyStored().call();
```

Call "payable" methods like this.

```text
    const one = new BN('1')
    let options = {
		gasPrice: 1000000000,
		gasLimit: 210000,
		value: toWei(one, hmy.utils.Units.one),
    };
    
    const increment = await contract.methods.addMoney().send(options)
```

**Congratulations** you have now connected your one wallet, and completed writing code for it to interact with the harmony blockchain.

