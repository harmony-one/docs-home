# Math Wallet

## Installation

The completed code can be found [here](https://github.com/rachit2501/Smart-Contract-Demo/tree/master/Math%20Wallet).

Download Math Wallet from [here](https://chrome.google.com/webstore/detail/math-wallet/afbcbjpbpfadlkmhmclhkeeodmamcflc). Follow the instructions and setup your wallet.

For setting up your own project just replace the code in `userWallet.js` in One Wallet guide with the following:

```javascript
const { fromBech32 } = require('@harmony-js/crypto');
const defaults = {};

export class MathWallet {

	constructor(network, client) {
		console.log(network, client);
		this.isMathWallet = false;
	}

	 signIn() {
		if (!this.mathwallet) {
			this.initWallet();
		}

		this.mathwallet.getAccount().then((account) => {
			this.sessionType = `mathwallet`;
			this.address = account.address;
			this.isAuthorized = true;
			return Promise.resolve();
		});
	}

	 initWallet() {
		this.isMathWallet = window.harmony && window.harmony.isMathWallet;
		this.mathwallet = window.harmony;
		this.signIn();
	}

	 async signTransaction(txn) {
		console.log(this.isMathWallet);
		if (this.sessionType === 'mathwallet' && this.isMathWallet) {
			console.log(this.mathwallet);
			return this.mathwallet.signTransaction(txn);
		}
	}

	 attachToContract(contract) {
		contract.wallet.createAccount();

		if (contract.wallet.defaultSigner === '') {
			contract.wallet.defaultSigner = this.address;
		}

		contract.wallet.signTransaction = async (tx) => {
			try {
				tx.from = this.address;
				const signTx = await this.signTransaction(tx);
				console.log(signTx);
				return signTx;
			} catch (err) {
				if (err.type === 'locked') {
					alert(
						'Your MathWallet is locked! Please unlock it and try again!'
					);
					return Promise.reject();
				} else if (err.type === 'networkError') {
					await this.signIn();
					this.initWallet();

					try {
						tx.from = this.address;
						const signTx = await this.signTransaction(tx);
						return signTx;
					} catch (error) {
						return Promise.reject(error);
					}
				} else {
					alert(
						'An error occurred - please check that you have MathWallet installed and that it is properly configured!'
					);
					return Promise.reject();
				}
			}
		};

		return contract;
	}
}
```
