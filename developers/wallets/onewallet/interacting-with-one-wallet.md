---
description: This section covers how to interact with one wallet extension.
---

# Interacting with One Wallet

> We are assuming here that you are following the same setup as mentioned in the previous section.

Go to you `src/init.js` and add the following code.

```text
import userWallet from './userWallet';

let but = document.getElementById("inputtButton");

but.addEventListener("click",initWallet);

async function initWallet(){
    const wallet = new userWallet();
    await wallet.signin();
}
```

Here we have simply attached a "click" listener before initiating code to interact with the Wallet.

### Detecting one wallet and interacting with it.

When user loads a page, one wallet automatically inject a `onewallet` object into the `window` object of your browser. We use this to interact with the same.

> In our example, following code is implemented in `src/userWallet.js`

Object to interact with one wallet can be accessed sing the following.

```text
 const isOneWallet = window.onewallet && window.onewallet.isOneWallet;
 const onewallet = window.onewallet;
```

The `onewallet` object needs a `defaultsigner` for signing the transactions, and lastly `signTransaction` object . We do the following using the following code snippets.

```text
 const getAccount = await this.onewallet.getAccount();
 await this.connectToOneWallet(this.onewallet)
```

```text
   async signin(){
        const getAccount = await this.onewallet.getAccount();
        console.log("slkdfjds")
        console.log(getAccount)

        this.address = getAccount.address;
        this.isAuthorized = true;
    }
```

The final code we have in our example is as follows. `src/userWallet.js` 

```text
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

You can now successfully interact with the one wallet browser extension.

For more examples checkout this [link](https://github.com/harmony-one/sdk/tree/master/packages/harmony-core).

