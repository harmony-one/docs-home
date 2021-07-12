---
description: CLI (Command Line) Version of 1Wallet
---

# CLI Guide

Go to [https://github.com/polymorpher/one-wallet/releases/tag/v0.1-cli](https://github.com/polymorpher/one-wallet/releases/tag/v0.1-cli) and download the file that is appropriate to your operating system \(1wallet-linux, 1wallet-macos, or 1wallet-win.exe\).

* I saved it in my downloads folder, but you can save it anywhere.
* Open your Terminal \(I'm a Mac user\), and run the following commands:

```text
cd downloads

chmod +x ./1wallet

./1wallet
```

Now that you have installed your CLI 1Wallet, you can do several things including:

```text
Commands:
  
./1wallet scan                            Build a new wallet and show its setup 
                                          QR code in terminal

./1wallet make <recovery-address> <code>  Deploy the wallet you just built to 
                                          blockchain and make it your "main" 
                                          wallet

./1wallet send <address> <amount> <code>  Send funds to another address

./1wallet main <wallet>                   Change "main" wallet

./1wallet list                            Show all wallets (address, name,
                                          balance)

Options:
      --help      Show help                                           [boolean]
  -n, --network   The network you want to use. Can be mainnet, testnet, or any
                  valid URL                       [string] [default: "mainnet"]
  -r, --relayer   The relayer you want to use. Can be "beta" (hosted by ONE
                  Wallet) or any valid URL           [string] [default: "beta"]
  -p, --password  The password for accessing the Relayer. Default is
                  "onewallet" which is password for the "beta" relayer hosted
                  by ONE Wallet.                [string] [default: "onewallet"]
  -w, --wallet    The wallet you are going to use for transfer funds. By
                  default, the main wallet is used, which is the last wallet
                  you created                                          [string]
  -s, --store     Path of which your wallet data is stored. By default the data
                  is stored in a subdirectory "wallets" where this command line
                  tool is executed.               [string] [default: "wallets"]
      --version   Show version number                                 [boolean]
```

Let us know if you find any issues: [https://github.com/polymorpher/one-wallet/issues](https://github.com/polymorpher/one-wallet/issues)

