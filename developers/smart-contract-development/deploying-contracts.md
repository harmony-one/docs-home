# Deploying Contracts using DApp Examples

## Running the admin portal

```text
cd /Users/johnwhitton/projects/sdk/dapp-examples/web
yarn start
```

You will get something like this

```text
$ cd Backend && yarn install && yarn build:server && node build/index.js
[1/4] 🔍  Resolving packages...
success Already up-to-date.
$ rm -rf build && ./node_modules/.bin/babel src -d build
Successfully compiled 13 files with Babel.
❌  Server-side HMR Not Supported.
express http is listening on 3000
```

Open the browser and go to `http://localhost:3000` and select contracts from the left side menu.

![Contract Portal](https://github.com/harmony-one/docs-home/tree/041b67b5a621ad2463849889d9d29b3bb7789032/.gitbook/assets/screen-shot-2019-08-05-at-8.10.24-pm.png)

To deploy a contract select the detail Action on the right

![Contract admin portal](https://github.com/harmony-one/docs-home/tree/041b67b5a621ad2463849889d9d29b3bb7789032/.gitbook/assets/screen-shot-2019-08-05-at-8.11.54-pm.png)

Then select the deploy button and enter your private key, for example

```text
01F903CE0C960FF3A9E68E80FF5FFC344358D80CE1C221C3F9711AF07F83A3BD
```

This will show you your balance and then you can press send to deploy the contract

![Deploying a contract](https://github.com/harmony-one/docs-home/tree/041b67b5a621ad2463849889d9d29b3bb7789032/.gitbook/assets/screen-shot-2019-08-05-at-8.13.59-pm.png)

This will deploy the contract and when successful you can see the information below by scrolling down.

![Deployed contract](https://github.com/harmony-one/docs-home/tree/041b67b5a621ad2463849889d9d29b3bb7789032/.gitbook/assets/screen-shot-2019-08-05-at-8.18.52-pm.png)

You then can set the latest deployed contract as the default by using the `set contract` action on the right. It will prompt you for a confirmation as follows.

![Confirming the setting of the default contract](https://github.com/harmony-one/docs-home/tree/041b67b5a621ad2463849889d9d29b3bb7789032/.gitbook/assets/screen-shot-2019-08-05-at-8.22.17-pm.png)

