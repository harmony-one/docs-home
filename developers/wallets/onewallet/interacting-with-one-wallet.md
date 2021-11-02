---
description: This section covers how to interact with Harmony Chrome Extension Wallet
---

# Interacting with Harmony Chrome Extension Wallet

> We are assuming here that you are following the same setup as mentioned in the previous section.

Go to you `src/init.js` and add the following code.

```
import userWallet from './userWallet';

let but = document.getElementById("inputtButton");

but.addEventListener("click",initWallet);

async function initWallet(){
    const wallet = new userWallet();
    await wallet.signin();
}
```

Here we have simply attached a "click" listener before initiating code to interact with the Wallet.

### Detecting Harmony Chrome Extension Wallet and interacting with it.

When user loads a page, Harmony Chrome Extension Wallet automatically inject a `onewallet` object into the `window` object of your browser. We use this to interact with the same.

> In our example, following code is implemented in `src/userWallet.js`

Object to interact with Harmony Chrome Extension Wallet can be accessed sing the following.

```
 const isOneWallet = window.onewallet && window.onewallet.isOneWallet;
 const onewallet = window.onewallet;
```

The `onewallet` object needs a `defaultsigner` for signing the transactions, and lastly` signTransaction` object . We do the following using the following code snippets.

```
 const getAccount = await this.onewallet.getAccount();
 await this.connectToOneWallet(this.onewallet)
```

```
   async signin(){
        const getAccount = await this.onewallet.getAccount();
        console.log("slkdfjds")
        console.log(getAccount)

        this.address = getAccount.address;
        this.isAuthorized = true;
    }
```

The final code we have in our example is as follows. `src/userWallet.js`&#x20;

```
import  hmy  from './hmy';

class userStore {
     
    constructor (stores) {
        this.isOneWallet = window.onewallet && window.onewallet.isOneWallet;
        this.onewallet = window.onewallet;
    }

    async signin(){
        const getAccount = await this.onewallet.getAccount();
        console.log("slkdfjds")
        console.log(getAccount)

        this.address = getAccount.address;
        this.isAuthorized = true;
    }

}

export default userStore
```

### Congratulations !!

You can now successfully interact with the Harmony Chrome Extension Wallet.

For more examples checkout this [link](https://github.com/harmony-one/sdk/tree/master/packages/harmony-core).
