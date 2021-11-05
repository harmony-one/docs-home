# WalletConnect

[WalletConnect](https://walletconnect.com) is standard api widely used by Trustwallet, Binance, Kava, and other apps to connect mobile wallet with Dapps.

Most existing connect works with a minor modification: allow support for Harmony chainId. (example [Viperswap PR](https://github.com/VenomProtocol/venomswap-interface/pull/36))

### Adding Harmony chains
```
export const walletconnect = new WalletConnectConnector({
  rpc: {
    1: NETWORK_URL,
    [ChainId.HARMONY_MAINNET]: 'https://api.s0.t.hmny.io/',
    [ChainId.HARMONY_TESTNET]: 'https://api.s0.b.hmny.io'
  },
  bridge: 'https://bridge.walletconnect.org',
  qrcode: true,
  supportedChainIds: [
    ChainId.HARMONY_MAINNET, // harmony
    ChainId.HARMONY_TESTNET // harmony testnet
  ]
})
```

### Full Dapp implementation

Follow the tutorials on https://docs.walletconnect.com for the respective platform.

For web, there is a reference implementation available at https://github.com/hashmesan/sef-walletconnect-example-dapp

Live demo: https://hashmesan.github.io/sef-walletconnect-example-dapp/

### Current supported mobile wallets

* [Sef Wallet](https://sefwallet.one) - Harmony Defi Wallet