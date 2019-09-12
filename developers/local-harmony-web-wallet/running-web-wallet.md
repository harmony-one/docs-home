# Running Web Wallet

## Pre-requisites

{% hint style="info" %}
Clone the [dapp-examples](https://github.com/harmony-one/dapp-examples) repository
{% endhint %}

{% hint style="info" %}
Ensure you have cloned and installed the[ dapp-examples](https://github.com/harmony-one/dapp-examples) according to the [readme](https://github.com/harmony-one/dapp-examples/blob/master/README.md).
{% endhint %}

## Pointing the web wallet to your local harmony instance

{% hint style="info" %}
Currently you need to modify [network.ts](https://github.com/harmony-one/dapp-examples/blob/master/web/WebWallet/src/models/network.ts) to point the webwallet to your local harmony node. You do this by setting the index to zero `const index = 0;`
{% endhint %}

{% hint style="info" %}
**Please note** any time you restart your local harmony node you will need to reset the nonce in the webwallet. This is currently done by going to the browser, opening the developer tools and typing `localStorage.clear()` in the console.
{% endhint %}

![Clearing the nonce when restarting your local harmony network](https://github.com/harmony-one/docs-home/tree/041b67b5a621ad2463849889d9d29b3bb7789032/.gitbook/assets/screen-shot-2019-08-05-at-6.55.16-pm.png)

```text
const defaultProviders = [
  {
    id: ChainID.Default,
    type: ChainType.Harmony,
    name: 'Harmony TestNet',
    http: 'http://localhost:9500',
    ws: 'ws://localhost:9800',
  },
  {
    id: ChainID.Ropsten,
    type: ChainType.Ethereum,
    name: 'Ropsten',
    http: 'https://ropsten.infura.io/v3/4f3be7f5bbe644b7a8d95c151c8f52ec',
    ws: 'wss://ropsten.infura.io/ws/v3/4f3be7f5bbe644b7a8d95c151c8f52ec',
  },
];

const index = 0;

export default {
  namespace: 'network',
  state: {
    providerList: [...defaultProviders],
    selected: 'Harmony TestNet',
    messenger: new Messenger(
      new WSProvider(defaultProviders[index].ws),
      defaultProviders[index].type,
      defaultProviders[index].id,
    ),
  },
```

## Running the Wallet

```text
cd /Users/johnwhitton/projects/sdk/dapp-examples/web/WebWallet
yarn install
yarn start
```

You should see something like the following

```text
johns-mbp:WebWallet johnwhitton$ yarn start
yarn run v1.17.3
$ umi dev

✔ Webpack
  Compiled successfully in 7.43s

Starting the development server...

 DONE  Compiled successfully in 7439ms                                                                                                                                                                                              4:18:19 PM


  App running at:
  - Local:   http://localhost:8000/ (copied to clipboard)
  - Network: http://192.168.86.23:8000/

 WAIT  Compiling...                                                                                                                                                                                                                 4:18:19 PM


✔ Webpack
  Compiled successfully in 337.91ms

 DONE  Compiled successfully in 338ms
```

Open a web browser at the local wallet. You should see the following

![Harmony Web Wallet initial screen](https://github.com/harmony-one/docs-home/tree/041b67b5a621ad2463849889d9d29b3bb7789032/.gitbook/assets/screen-shot-2019-08-05-at-6.14.19-pm.png)

