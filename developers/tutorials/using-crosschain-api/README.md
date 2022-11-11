# Using Crosschain API

This API will let you swap assets between different chains, this is the current status:

**Version: B0.1**

* This version allow you to swap BUSD in Ethereum into BUSD in Binance, we thought this is a good first step because it will serve as a vehicle between any assets between the two networks.
* Testnets required for running this versions are:
  * Harmony Testnet ([https://api.s0.b.hmny.io](https://api.s0.b.hmny.io))
  * Ethereum Kovan ([https://kovan.infura.io/v3/acb534b53d3a47b09d7886064f8e51b6](https://kovan.infura.io/v3/acb534b53d3a47b09d7886064f8e51b6))
  * BSC Testnet ([https://docs.binance.org/smart-chain/developer/rpc.html](https://docs.binance.org/smart-chain/developer/rpc.html))

## Some Basic Instructions

* Right now you see two folders, `webserver` and `testing`. The former contains the webserver that must be started to call the API endpoints locally in you machine (read [this](https://docs.harmony.one/home/developers/tutorials/using-crosschain-api/webserver) for more detailed instructions), the latter contains scripts in `javascript` and `postman` that can be used to test the endpoints once you have the webserber running. It also has examples of how to make calls to the API.
* You will need to set `.env` files in both folders, we are adding samples for those files (they are called `env_file`), so you can just go ahead and rename them to `.env`. You will also need to add your private key to the `.env` file in the testing folder if you plan to use the `.js` file. If you plan to use postman, you will need to paste it into the workspace, so make sure that you create it outside the repo. In any case we encourage you to add `.env` files to the `.gitignore` and never paste you private keys in the code.

Enjoy!
