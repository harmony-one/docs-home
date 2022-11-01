# How to find a bridged token address

You can avoid this process if you use Add token to Metamask button on the bottom your bridge operation page after operation is completed:

![add\_token.png](../../../../.gitbook/assets/add\_token.png)

You can find your token from your final step transaction (mint/unlock) if it’s correctly displayed (sometimes there are delays in data representation).There is a token symbol near the amount in “Tokens transferred”/ ”Token transfers” section that leads to the token page.

![token explorer eth.png](../../../../.gitbook/assets/token\_explorer\_eth.png)

![token explorer hmy.png](../../../../.gitbook/assets/token\_explorer\_hmy.png)

You can also look for the token in a token list on your wallet address page in the target chain explorer (it also can take some time for a token to appear).

![Screenshot 2022-01-20 at 23.41.56.png](../../../../.gitbook/assets/Screenshot\_2022-01-20\_at\_23.41.56.png)

![Screenshot 2022-01-20 at 23.46.25.png](../../../../.gitbook/assets/Screenshot\_2022-01-20\_at\_23.46.25.png)

Click on the token symbol, and you’ll see all necessary token information.

![Screenshot 2022-01-20 at 21.52.12.png](../../../../.gitbook/assets/Screenshot\_2022-01-20\_at\_21.52.12.png)

![Screenshot 2022-01-20 at 21.45.29.png](../../../../.gitbook/assets/Screenshot\_2022-01-20\_at\_21.45.29.png)

Don’t forget, that address should be in **ETH style** (starting **0x**...). For Harmony Explorer, there is a switcher in the top right corner.

If you can’t find your token there, please use this page to find a token address you should have after the bridge: [**What token will I get after bridge?**](what-token-will-i-get-after-bridge.md))

Search by a token you had before the bridge operation.

Note that if your token is mapped to one network and you bridged it to another, you most likely got not liquid token that you need to bridge back. Same thing is for the case you chose wrong token type. For example, if you bridge ONE as BEP20, you receive bscONE that is not a liquid token.

After you find your token, add it to your wallet as shown [here](https://docs.harmony.one/home/general/horizon-bridge/adding-tokens).

Check that you add token to a receiver wallet of your operation and the wallet is connected to the correct network.
