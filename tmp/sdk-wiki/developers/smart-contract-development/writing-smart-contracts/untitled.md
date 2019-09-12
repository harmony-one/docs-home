---
description: truffle-config.js
---

# truffle-config.js

Note if you use `phrase` with your mnemonic then `privateKey` is optional.

{% hint style="info" %}
**Note - this sample code is as an example only**

Private Keys should always be secured and never committed into public repositories.
{% endhint %}

```text
const { TruffleProvider } = require('@harmony-js/core')

const phrase =
  'urge clog right example dish drill card maximum mix bachelor section select'
const privateKey =
  '01F903CE0C960FF3A9E68E80FF5FFC344358D80CE1C221C3F9711AF07F83A3BD'
const url = `http://localhost:9500`

/**
 * Use this file to configure your truffle project. It's seeded with some
 * common settings for different networks and features like migrations,
 * compilation and testing. Uncomment the ones you need or modify
 * them to suit your project as necessary.
 *
 * More information about configuration can be found at:
 *
 * truffleframework.com/docs/advanced/configuration
 *
 * To deploy via Harmony-betanet you'll need a wallet provider (like truffle-hdwallet-provider)
 * to sign your transactions before they're sent to a remote public node.
 *
 * You'll also need a mnemonic - the twelve word phrase the wallet uses to generate
 * public/private key pairs. If you're publishing your code to GitHub make sure you load this
 * phrase from a file you've .gitignored so it doesn't accidentally become public.
 *
 */

module.exports = {
  /**
   * Networks define how you connect to your ethereum client and let you set the
   * defaults web3 uses to send transactions. If you don't specify one truffle
   * will spin up a development blockchain for you on port 9545 when you
   * run `develop` or `test`. You can ask a truffle command to use a specific
   * network from the command line, e.g
   *
   * $ truffle test --network <network-name>
   */

  networks: {
    // Useful for testing. The `development` name is special - truffle uses it by default
    // if it's defined here and no other network is specified at the command line.
    // You should run a client (like ganache-cli, geth or parity) in a separate terminal
    // tab if you use this network and you must also set the `host`, `port` and `network_id`
    // options below to some value.
    //
    development: {
      // host: 'localhost', // Localhost (default: none)
      // port: 9500, // Standard Ethereum port (default: none)
      network_id: '1', // Any network (default: none)
      provider: () => {
        const truffleProvider = new TruffleProvider(url, phrase)
        const newAcc = truffleProvider.addByPrivateKey(privateKey)
        truffleProvider.setSigner(newAcc)
        return truffleProvider
      }
    }

  },

  // Set default mocha options here, use special reporters etc.
  mocha: {
    // timeout: 100000
  },

  // Configure your compilers
  compilers: {
    solc: {
      // version: '0.5.1', // Fetch exact version from solc-bin (default: truffle's version)
      // docker: false, // Use "0.5.1" you've installed locally with docker (default: false)
      // settings: {
      //   // See the solidity docs for advice about optimization and evmVersion
      //   optimizer: {
      //     enabled: false,
      //     runs: 200,
      //   },
      //   evmVersion: 'homestead',
      // },
    }
  }
}
```

