# Connect Metamask to the Harmony chain

Developers can use this sources to provide users easy configure or switch to correct Harmony chain and shard. \(by analogy with [https://chainlist.org/](https://chainlist.org/)\)

```javascript
const chainId = 2; // 0-3 - harmony chain

window.web3.eth.getAccounts((e, t) => {
  window.ethereum.request({
    method: 'wallet_addEthereumChain',
    params: [
      {
        chainId: '0x' + Number(1666600000 + chainId).toString(16),
        chainName: Harmony Mainnet Shard ${chainId},
        nativeCurrency: { name: 'ONE', symbol: 'ONE', decimals: 18 },
        rpcUrls: [https://s${chainId}.api.harmony.one],
        blockExplorerUrls: ['https://www.harmony.one/'],
      },
      t[0],
    ],
  });
});
```

After call this method - user will see message to approve adding or switching to correct Harmony chain.

You can see more information about this api here [https://docs.metamask.io/guide/rpc-api.html\#wallet-addethereumchain](https://docs.metamask.io/guide/rpc-api.html#wallet-addethereumchain)

