# Hack the Horizon

## First Place

### Kawaii Battle Royale <a href="#f251" id="f251"></a>

[Kawaii Battle Royale](https://github.com/OpenDive/KawaiiBattleRoyaleSwitchBullet\_Dapp) (KBR) is a NO-LOSS team-based first-person shooter DeFi Game that runs on the Harmony blockchain and bridges liquidity from Harmony and Ethereum money markets such as AAVE and CREAM Finance.

The game is similar to Overwatch or Fortnite, except that weekly and monthly “interest-bearing ESports no-loss tournaments” are ran, where users stake their entries (BUSD) into a tournament.

![](<../../../../.gitbook/assets/image (231).png>)

The pooled BUSD entries are then transferred from Harmony to the highest-yield earning money market on Ethereum (e.g. AAVE or CREAM) to earn interest. The interest is then used as the tournament’s reward — hence the term “no-loss”. Once the tournament ends, all staked entries are refunded back to the users.

![](<../../../../.gitbook/assets/image (232).png>)

Further, characters, weapons and skins are tokenized as NFTs and available for trading in our marketplace.

Kawaii Battle Royale: Switch Bullet is only the first season of this game, and of many more to come. Keep an eye for the next season! :)

### VergeNet <a href="#f9de" id="f9de"></a>

[VergeNet](https://gitcoin.co/hackathon/hack-the-horizon/projects/4180/VergeNet) is a zkSNARKS based Scalable and Secure Provers and Verifiers for Ethereum — Harmony Horizon Bridge.

Key Points:

* A bridge with cross-chain light clients, relayers, and prover full nodes, all trustless, no additional trust assumptions beyond the two blockchains that the bridge is connected to.
* A gas-efficient Harmony light client on Ethereum (could be generalized to other chains) that only requires checkpoint blocks (1 block every x blocks, where 1 ≤ x ≤ 16384, 16384 is the #blocks per epoch) to verify any number of Harmony transaction proofs by the clients.
* A constant-size Harmony light client proof that any user needs to send cross-chain (e.g., Ethereum) to claim their Harmony transaction.

[Check out their github](https://github.com/LatticeLabVentures/VergeNet) to see more details.

### LendingSwap <a href="#a293" id="a293"></a>

[Lending Swap](https://github.com/trinhtan/horizon-hackathon) is an application used to swap atoms between tokens, native tokens from Ethereum to Harmony and vice versa. Between two bridges of Ethereum — Harmony, there are 2 relayers to be able to mint corresponding tokens when swapping between the two platform. There will be validators at each bridge to verify the atomic swaps, when 75% consensus is reached, the transaction will be executed by the relayer. In order to be able to transfer the equivalent value of tokens, for example ETH <> ONE, KNC (ERC20) <>WETH (HRC20), we use price data taken from Band Oracle.

Ethereum to Harmony:

* ETH -> ONE
* ETH -> Wrapped ETH
* ERC20 -> ONE
* ERC20 -> HRC20
* Wrapped ONE (ERC20) -> ONE

![](<../../../../.gitbook/assets/image (233).png>)

Harmony to Ethereum:

* ONE -> ETH
* ONE -> Wrapped ONE
* HRC20 -> ERC20
* Wrapped ETH (HRC20) -> ETH
* HRC20 -> ETH

### SeeForex <a href="#90cd" id="90cd"></a>

[SeeForex](https://github.com/kuyawa/seeforex) is a currency exchange for trading fiat tokens at market price. It allows buying and selling currencies with just one click and transaction confirmations occur within seconds thanks to the fastest blockchain protocol Harmony Network.

{% embed url="https://youtu.be/AxbSbTn67Z4" %}

## Second Place <a href="#ee73" id="ee73"></a>

[_LegalAge_](https://github.com/sladecek/harla\_demo) is a privacy-preserving age-verification service based on [zero knowledge](https://www.zeroknowledge.fm/) cryptography and the [Harmony One](https://www.harmony.one/) blockchain. Many people feel uncomfortable to show a passport or an ID-card to strangers, because they can be stalked or their document may be secretly photocopied and their identity stolen. Using the service, anyone can prove that they are older or younger than certain age without presenting an ID or telling the exact date of birth.

View the [demo here](https://gitcoin.co/hackathon/hack-the-horizon/projects/4186/LegalAge).

![Image for post](https://miro.medium.com/max/4696/1\*V6xeQV-GgSaQHSck6035MQ.png)

### GitMony <a href="#2132" id="2132"></a>

[GitMony](https://github.com/BakaOtaku/git\_mony) uses Harmony Bridge and Chainlink oracle, to make a completely decentralized platform to reward opensource contributors.

{% embed url="https://youtu.be/M7-3AImM8mI" %}

GitMony is a truly decentralized platform to reward this and uses Chainlink and Harmony to verify the contributions on Github. The organization will have to register on the smart-contract and its HRC20 coins named (Doke Coin) will be deposited into the contract. Now a contributor will commit on the organisation’s repo and also prefix his public key to the commit message. Then the contributor will have to call the smart contract from his wallet and provide the info of his repo to which he has committed and also the commit hash. Now chainlink will verify the commit from github and if the wallet address on the commit message and the smart-contract caller’s address match then the HRC20 tokens will be transferred to the sender to reward the contributor.

### OpenFi <a href="#24ca" id="24ca"></a>

[OpenFi](https://github.com/Alexgrsjn/OpenFi) plans to give Users the ability to manage their tokens on Harmony Blockchain the same way a bank web-portal allows you to manage your different bank accounts.

You can use the [demo here](https://openfi.dev/#/).

OpenFi plans to bring a Fiat gateway, secure pegged decentralized cryptocurrencies (ex: USD, CHF, EUR etc), Nfc solution that allows user to write their own cards and accept payment on aready exitant POS terminals //the whole idea is provide an OPEN banking solution with Low fees (taking advantage of 2s finality) have Easy access of Decentralized exchanges directly on the OpenFi Dashboard have a simplified interface or candle chart for users who want to trade) //will start with a fork of uniswap. iv been thinking about porting DyDx too

### SwoopDex <a href="#7147" id="7147"></a>

Integration of Band Standard Dataset reference price data enables users to determine if they are getting a good trade on [Swoop DEX](https://github.com/Dodecane/swoop-interface). Additionally, it also helps users determine the correct ratio of tokens to provide when they are the first liquidity provider. Integration of Binance.us price data and providing direct links to relevant trading pairs exposes users to arbitrage opportunities, increasing the efficiency of Swoop DEX.

{% embed url="https://youtu.be/1wethoG_2XQ" %}

### Token Rewards Distribution

[Token Rewards Distribution](https://github.com/ysongh/Token-Reward-Distribution) is a web app that allow users to send rewards as erc20 token to others with low transaction fees using Horizon Bridge.

View the [video here](https://gitcoin.co/hackathon/hack-the-horizon/projects/4170/Token-Reward-Distribution).

### Binance US Harmony API Dapp <a href="#3958" id="3958"></a>

Use of Binance.us API on Harmony using React : \* API call from @harmony-js/core \* API call from @binance-api-react-native \* API call from Axios

### The E-H Honey <a href="#b0b1" id="b0b1"></a>

[E-H Honey](https://github.com/azizyano/THE-E-H-Honey) is an app where you can BEE TOKEN and stake it in any chain you want Etheruem or harmony the reward will be the HNY TOKEN uses Harmony’s bridge ETH<->ONE to jump from chain to another.

## Third Place <a href="#875b" id="875b"></a>

There were five 3rd place winners:

* [Port Augur to Harmony](https://gitcoin.co/hackathon/hack-the-horizon/projects/3856/port-the-augur-protocol-and-ui-to-harmony-chain): Dev ported Augur to Harmony.
* [Nodejs CLI for the Harmony Rosetta Endpoints](https://github.com/zyra-zia/harmony-rosetta-cli): Dev created a command line interface for Harmony Rosetta.
* [Bet to Win 2x](https://github.com/azizyano/Bet\_to\_win\_x2): Betting game where you can win 2x your bet size.
* [Harmony Rosetta CLI in Python](https://github.com/blockjoe/harmony-api-client-python): A command line interface for Harmony Rosetta written in Python.
* [Harmony Explorer](https://github.com/CryptoDizzy/Harmony-Explorer): Dev built a Harmony Block Explorer.
