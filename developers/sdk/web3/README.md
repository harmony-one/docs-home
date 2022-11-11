---
description: Using web3.js with harmony protocol.
---

# Web3.js

## Introduction

[Web3.js](https://web3js.readthedocs.io/en/v1.3.0/) is a set of libraries that allow developers to interact with Ethereum nodes using HTTP, IPC or WebSocket protocols. Harmony has an Ethereum-like API available that is fully compatible with Ethereum-style JSON RPC invocations. Therefore, developers can leverage this compatibility and use the web3.js library to interact with a Harmony node as if they were doing so on Ethereum.

### Setup Web3.js with Harmony <a href="#setup-web3js-with-moonbeam" id="setup-web3js-with-moonbeam"></a>

To get started with the web3.js library, we first need to install it using the following command:

```
npm install web3
```

Once done, the simplest setup to start using the library and its methods is the following:

```javascript
const Web3 = require('web3');

//Create web3 instance
const web3 = new Web3(HMY_RPC_URL);
```

Depending on which network you want to connect to, you can set the `HMY_RPC_URL` to the following values:

For Mainnet:&#x20;

```javascript
HMY_RPC_URL = https://api.s0.t.hmny.io
```

For Testnet:

```javascript
HMY_RPC_URL = https://api.s0.b.hmny.io
```

## Tutorials

In the case that you are interested in a more detailed step-by-step guide, you can go to our specific tutorials on using web3.js on a Harmony: &#x20;

{% content-ref url="send-transaction.md" %}
[send-transaction.md](send-transaction.md)
{% endcontent-ref %}

{% content-ref url="find-the-last-transaction.md" %}
[find-the-last-transaction.md](find-the-last-transaction.md)
{% endcontent-ref %}

The steps can also be adapted to deploy on the Harmony Testnet, by using the correct `RPC_URL` as mentioned before.

{% hint style="info" %}
You can use all the library functions described in the official [Web3 documentation](https://web3js.readthedocs.io/en/v1.3.0/).&#x20;
{% endhint %}
