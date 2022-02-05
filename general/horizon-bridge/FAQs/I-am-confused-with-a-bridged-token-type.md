# I’m confused with a bridged token type

If you received something you didn’t suppose to get, first, look if your token has any liquidity. You might not expect to receive a mapped token if you didn’t read about mapped tokens before the operation. Look here if you got a token you supposed to get after the bridge:  [**What token will I get after bridge?**](What-token-will-I-get-after-bridge.md). You can get use of your mapped token. Look for swapping options in swap or exchange services such as [Viperswap](https://viperswap.one/#/swap) or ask about available DEX in the Harmony community groups. If there are no options that suit your interests, you can bridge your tokens back. If you don’t know how to bridge back see [I don’t know how to bridge my token](I-dont-know-how-to-bridge-my-token.md). 

There are also cases when a token was bridged with the wrong settings and wrapped in a way that it lost its liquidity (1bscDAI, bsc1UST, etc). In this situation, you need to bridge your tokens back to remove an extra wrap. For example, if you bridge ONE as BEP20, you get bscONE token instead of Native ONE. 

It also can happen if you bridge your token to the wrong network. For example, Ethereum [BUSD](https://etherscan.io/token/0x4fabb145d64652a948d72533023f6e7a623c7c53) token is mapped with [BUSD](https://explorer.harmony.one/address/0xE176EBE47d621b984a73036B9DA5d834411ef734?activeTab=3) on Harmony, and [BUSD](https://bscscan.com//token/0xe9e7CEA3DedcA5984780Bafc599bD69ADd087D56) from Binance is mapped with [bscBUSD](https://explorer.harmony.one/address/0x0aB43550A6915F9f67d0c454C2E90385E6497EaA?activeTab=3) on Harmony.

![Screenshot 2022-01-20 at 21.43.25.png](../../../.gitbook/assets/Screenshot_2022-01-20_at_21.43.25.png)

You can’t get a liquid token on Binance from [BUSD](https://explorer.harmony.one/address/0xE176EBE47d621b984a73036B9DA5d834411ef734?activeTab=3) which originated from the Ethereum, and bscBUSD won’t be liquid on Ethereum: token will get an extra wrap. 

If you have an incorrectly bridged token with an extra wrap, see [How to bridge back an incorrectly bridged token](How-to-bridge-back-an-incorrectly-bridged-token.md). 

Note that if there is a wrap originated in the Ethereum or Binance network, you can’t get rid of it in Harmony. You need to unwrap it before the bridge. For example, for WETH you receive 1WETH on Harmony.