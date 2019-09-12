# Interacting with Deployed Contracts using DApp Examples

We have now deployed the lottery contract and so the next step is to run the lottery DApp to interact with the contract.

To run the lottery app enter the following commands

```text
cd /Users/johnwhitton/projects/sdk/dapp-examples/web/Lottery
yarn start
```

You will see something similar to this

```text
johns-mbp:Lottery johnwhitton$ yarn start
yarn run v1.17.3
$ umi dev

✔ Webpack
  Compiled successfully in 5.89s

Starting the development server...

 DONE  Compiled successfully in 5897ms                                                                                                                                                                                              8:26:30 PM


  App running at:
  - Local:   http://localhost:8000/ (copied to clipboard)
  - Network: http://192.168.86.23:8000/

 WAIT  Compiling...                                                                                                                                                                                                                 8:26:30 PM


✔ Webpack
  Compiled successfully in 246.26ms

 DONE  Compiled successfully in 246ms
```

Open the lottery app by going to `http://localhost:8000` and you should see

![The lottery app](../../.gitbook/assets/screen-shot-2019-08-05-at-8.29.23-pm.png)

You then can sign in using your private key

```text
01F903CE0C960FF3A9E68E80FF5FFC344358D80CE1C221C3F9711AF07F83A3BD
```

![Log in using your private key](../../.gitbook/assets/screen-shot-2019-08-05-at-8.30.48-pm.png)

You will then be able to deposit

![You can now deposit](../../.gitbook/assets/screen-shot-2019-08-05-at-8.31.36-pm.png)

![Deposit ](../../.gitbook/assets/screen-shot-2019-08-05-at-8.32.15-pm.png)

And pick a winner

![Pick a winner](../../.gitbook/assets/screen-shot-2019-08-05-at-8.32.57-pm.png)

See the results

![](../../.gitbook/assets/screen-shot-2019-08-05-at-8.33.07-pm.png)

