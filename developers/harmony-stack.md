# Open Source Harmony Stack [WIP!] <!-- omit in toc -->

The goal of this page is to provide an overview of the open-source Harmony Tech Stack.

This is a living document and we are relying on our community to contribute to it and help maintain it. Please feel free to make edits and additions via pull requests. We apologize if we missed your project!

---

- [:clipboard: About](#clipboard-about)
- [:bookmark_tabs: Layers of Harmony Stack](#bookmark_tabs-layers-of-polkadot-stack)
  - [:iphone: User Interface](#iphone-user-interface)
  - [:wrench: Tools, APIs and Languages](#wrench-tools-apis-and-languages)
  - [:memo: Bridges, Fiat Gateways, Exchanges](#memo-bridges-fiat-gateways-exchanges)
  - [:nut_and_bolt: Platform Modules](#nut_and_bolt-platform-modules)
  - [:link: Crypto Projects](#link-crypto-projects)
  - [:black_nib: Signatures](#black_nib-signatures-and-cryptography)
  - [:satellite: Core Harmony Protocol](#satellite-core)
- [:construction_worker: Contributing](#construction_worker-contributing)

## :clipboard: About

The Harmony Tech Stack consists of the **open-source** technologies contributing to and relying on [Harmony](https://harmony.one). It is meant to be used for decentralized application (Dapp) development within numerous verticals including DeFi, Gaming, Provenance and many others not pictured below.

![Harmony Ecosystem](../.gitbook/assets/ecosystem_20.6.2021.png)

## :bookmark_tabs: Layers of Harmony Stack

In the below sections you can find a list of different layers of the Harmony Stack.

### :iphone: User Interface 

| Components | Existing projects | Potentially interesting projects
|-|-|-
|  Wallets | [Magic](https://magic.link/), [sprout](https://sprout.sesameseed.org/)|- social recovery & one-time-password authenticators for on-chain fund<br >- basic income & wealth from fixed-rate or high-yield investments  <br >- User-friendly Wallet based on  open millions to self-custody assets & collectibles without hardware, password or hack <br >- [Composable Authentication](https://github.com/hashmesan/harmony-totp) <br >- [Social onchain recovery](https://vitalik.ca/general/2021/01/11/recovery.html) <br >- [EIP-2938 Account abstraction implementation](https://github.com/harmony-one/bounties/issues/35) <br >- [on-device privacy](https://medium.com/@ronaldmannak/vivo-pay-a-zero-knowledge-payment-system-727997e4d25f) <br >- Keyless Security <br >- web3 integrations <br >- [Harmony Argent Integration](https://github.com/harmony-one/bounties/issues/31) 
| Browser Extensions | [Harmony One Wallet](https://github.com/harmony-one/one-wallet), [Math Wallet](https://mathwallet.org/web/harmony), [Metamask](https://metamask.io/) |
| Mobile Wallets|  [Frontier wallet](https://frontierwallet.com/), [Cobo Wallet](https://cobo.com/), [Math Wallet](https://mathwallet.org/), [7b](https://sevenb.io/) , [Guarda](https://guarda.com/), [Edge](https://edge.app/), [imtoken](https://token.im/?locale=en-us)
| Hardware Wallets | [Ledger](https://www.ledger.com/), [Trezor](https://trezor.io/), [SafePal](https://safepal.io/)
| Block Explorers | [Harmony Explorer](https://explorer.harmony.one/) |- [Modular Explorer supporting HRC20 and HRC721](https://github.com/harmony-one/bounties/issues/37)
| Validator Dashboards | [Smartstake](https://harmony.smartstake.io/)
| Node Explorers | [Watchdog](https://watchdog.hmny.io/report-mainnet)
| Staking Rewards | [Smartstake](https://harmony.smartstake.io/)
| Analytics | [The Graph](https://docs.harmony.one/home/developers/tools/the-graph) |- [Dune Analytics Integration](https://github.com/harmony-one/bounties/issues/39)
### :wrench: Tools, APIs and Languages

| Components | Existing projects | Potentially interesting projects
|-|-|-
| Easy Smart Contract Development | [Truffle](https://www.trufflesuite.com/), [Remix](https://remix.ethereum.org/), [Hardhat](https://hardhat.org/), [Decentology](https://www.decentology.com/)
| API | |- [API for Cross Chain Aggregation](https://medium.com/harmony-one/how-to-aggregate-cross-chain-liquidity-e2ef97ba2bf6)
| Client Libraries |
| Runtime Security |  | Automated Runtime checking tools, economic audit simulator such as [gauntlet.network](https://gauntlet.network/)

### :memo: Bridges, Fiat Gateways, Exchanges 

| Components | Existing projects | Potentially interesting projects
|-|-|-
| Bridges | [Ethereum ](https://bridge.harmony.one/), [Binance](https://bridge.harmony.one/), [Polkadot - Edgeware](https://talk.harmony.one/t/everstake-polkadot-harmony-bridge/918) |- [Trustless ONE BTC Bridge](https://docs.google.com/document/d/1Op1u9rbsR8sNwLblAYuFNONPCX5ODClVkOLt2mgBol0/edit#heading=h.wjz7s0uat2g5)  <br >- [Celo Optics Bridge](https://github.com/harmony-one/bounties/issues/33) <br >- [Solana Wormhole Bridge](https://github.com/certusone/wormhole) <br >- [Cosmos Gravity Bridge](https://github.com/cosmos/gravity-bridge) <br >- [Terra Shuttle Bridge](https://github.com/terra-money/shuttle) <br > - [DCRM Multichain Bridge](https://www.fusionite.info/post/dcrm-usecase-expanding-with-multichain-xyz)
| Fiat Gatways | [Wyre](https://www.sendwyre.com/), [Swapzone](https://swapzone.io/), [Changelly](https://changelly.com/), [switchchain](https://www.switchain.com/), [swft](https://www.swft.pro/#/),  [SimpleSwap](https://simpleswap.io/), [simplex](https://www.simplex.com/), [transak](https://transak.com/)
| Exchange Gateways | [Coinbase Rosetta](https://www.rosetta-api.org/) |- [Rosetta API Extension](https://github.com/harmony-one/bounties/issues/3)


### :nut_and_bolt: Platform Modules
| Components | Existing projects | Potentially interesting projects
|-|-|-
| Security | [Gnosis](https://gnosis.io/), [CertiK](https://www.certik.io/), [PeckShield](https://peckshield.com/en) |- [coq verified execution](https://dl.acm.org/doi/abs/10.1145/1452044.1452049) <br >- [information-flow: compositional reentrancy](https://www.cs.cornell.edu/andru/papers/oakland21/) <br >- [session types: language design](https://harmony.one/design) <br >- [smt: gas fee optimizer](https://twitter.com/stse/status/1328128280868708353)
| Oracle | [Chainlink](https://chain.link/), [Band Protocol](https://bandprotocol.com/), [API3](https://api3.org/)
| Privacy | [Dusk](https://dusk.network/), [Raze](https://www.raze.network/), [Webb Protocol](https://www.webb.tools/)
| Governance/DAO | [Harmony Governance](https://gov.harmony.one/#/)
| Cross Chain | |- [Cross Chain Arts and Collectibles](https://dappradar.com/blog/upland-and-blockchain-heroes-create-cross-chain-nft-cards)
| Finality | |- [Madhi Zamani Instachain](http://mahdiz.com/?i=1) <br >- [one second finality](https://github.com/harmony-one/bounties/issues/14)
| Name Service| [crazy.one names](https://github.com/harmony-one/one-names) |- [Name Service Key Address Resolution](https://medium.com/the-ethereum-name-service/ens-integration-spotlight-argent-bd8f9cf819f5)


### :link: Crypto Projects

| Components | Existing projects | Potentially interesting projects
|-|-|-
| DeFi | [Sushi](https://app.sushi.com/swap), [UMA Protocol](https://docs.umaproject.org/build-walkthrough/build-process), [daikiri finance](https://daikiri.finance/) | DEX with privacy and confidentiality features such as those found in a [dark pool](https://en.wikipedia.org/wiki/Dark_pool) 
| Automated Market Makers | [viperswap](https://viperswap.one/#/swap), [mochiswap](https://mochiswap.io/), [Reef](https://reef.finance/), [unifi](https://harmony.unifiprotocol.com/), [Injective Protocol](https://injectiveprotocol.com/), [JellySwap](https://jelly.market/), [SeeSwap](https://seeswap.one/), [OpenSwap](https://seeswap.one/), [LootSwap](https://lootswap.finance/), [swoop](https://swoop.exchange/)
| Lending | [AAVE](https://aave.com/)
| NFT | [Soccer Player](https://docs.harmony.one/home/developers/showcases/other-showcases#harmony-soccer-players), [Harmony One Punks](https://www.harmonypunks.one/) |- [NFT as a wallet profile](https://www.christies.com/features/10-things-to-know-about-CryptoPunks-11569-1.aspx) 
| MarketPlaces | [daVinci](https://davinci.gallery/), [Travala](https://whitepaper.travala.com/), [utu](https://utu.io/protocol/), [Ript.io](https://ript.io/), [lma-art-gallery](https://lma-art-gallery.com/) | - [ONE World: Geospatial NFT Marketplace](https://github.com/harmony-one/bounties/issues/48) <br >- [Smart Markets for NFT'S](https://hbr.org/2007/10/the-art-of-designing-markets) 
| Fixed Rate Incomie | | - [Staking Derivatives](https://research.paradigm.xyz/staking) <br >- [Fixed Rate Lending](https://twitter.com/stse/status/1378877524432707587) <br >-[Interest Rate Markets](https://twitter.com/stse/status/1380695737131020289) <br >- [Security Tranches](https://www.ledgerinsights.com/municipal-bonds-blockchain-tokenization-consensys-broker-acquisition/)
| Cross chain DeFi | |- [Interest Free Stablecoin](https://twitter.com/stse/status/1386794075123163137) <br >- [vaeriable-rate lending](https://docs.google.com/document/d/1i6KoxDMKKCy5zBwXVkkNgAxTUFZjBIboMQAZPBY7bRs/edit#) <br >- [Gas Fee Relay](https://github.com/harmony-one/bounties/issues/35) <br >- [Privacy Mixer](https://www.notion.so/Harmony-EVM-Mixer-w-Bulletproofs-fdc691363fa946c2a24ec3141258bd31)
| Staking | [Fuzz.fi](https://fuzz.fi/)
| Staking Derivatives | [Stafi](https://stafi.io/)
| Insurance | [DSLA Protocol](https://stacktical.com/)
| Multichain | [ViteDex](https://www.vite.org/), [Jellyswap](https://jelly.market/), [Dogen Finance](https://dogen.finance/)
| Lottery | [One Degen](https://onedegen.herokuapp.com/)
| Token Issuance | [Token Jenny](https://tokenjenny.one/)
| Charity | [Moonity](https://moonity.one/home#about)
| Real Estate | [Monopoly](https://mply.org/)
| Gaming | [Nano Royale](https://nanoroyale.com/), [freyala](https://www.freyala.com), [defi kingdoms](https://defikingdoms.com), [geriatrics gaming](https://geriatricsgaming.com)
| Gambling | [lootblocks](https://lootblocks.one)
| Multisig App Store | |- gnosis safe: multisig app store
| Payroll | |- [Decentralized Payroll Management for DAO's](https://medium.com/iearn/decentralized-payroll-management-for-daos-b2252160c543)
| Identity/DID | [Hypersign Identity](https://hypersign.id)
| Social Networking | |- [Social Referral](https://medium.com/terra-money/introducing-buzlink-scaling-social-referrals-5e08c2c65e8e)
| Governance/DAO | 
| Other | [Knit Finance](https://knit.finance/#token-economy), [MakiMoon](https://maki.one/why), [harmony validators](https://www.harmonyvalidators.com/)

### :black_nib: Signatures and Cryptography

| Components | Existing projects | Potentially interesting projects
|-|-|-
| Cryptography | |- [evmcurve bls12-381](https://notes.ethereum.org/@poemm/evm384-update5#Gas-Estimates-for-BLS12-381-Operations)
| Key Value Commitments | |- [Key Value Commitments](https://eprint.iacr.org/2020/1161)
| BulletProof | |- [EVM Mixer with Bulletproofs](https://www.notion.so/Harmony-EVM-Mixer-w-Bulletproofs-fdc691363fa946c2a24ec3141258bd31)
| Privacy | |- [poseidon hash precompile using curve25519](https://blog.harmony.one/privacy-on-harmony-powered-by-webb/)
| Light Clients| |- [superlight client, bootstrap without header sync](https://twitter.com/stse/status/1395033039168688134) <br >- [lightclient: epoch synch](https://medium.com/harmony-one/dusk-network-and-harmony-partner-to-build-towards-the-first-industry-grade-zero-knowledge-proof-c7b16f740a84)
| Zero Knowledge| |- [zksnark: plonk](https://medium.com/harmony-one/dusk-network-and-harmony-partner-to-build-towards-the-first-industry-grade-zero-knowledge-proof-c7b16f740a84)
| ethereum rollups | |- [zero knowledge proofs](https://zksync.io/) <br >- [zk porter l2 scaling](https://medium.com/matter-labs/zkporter-a-breakthrough-in-l2-scaling-ed5e48842fbf) <br >- [zk-zk-rollup](https://medium.com/aztec-protocol/aztecs-zk-zk-rollup-looking-behind-the-cryptocurtain-2b8af1fca619) <br >- [l2 for private transactions](https://zkopru.network/)


### :satellite: Core Harmony Protocol

| Components | Existing projects | Potentially interesting projects
|-|-|-
| Networking | |- [quic data transport](https://medium.com/harmony-one/harmonys-networking-story-7a83fb6f13ed) <br >- [hipv2 node identity](https://medium.com/harmony-one/harmonys-networking-story-7a83fb6f13ed) <br >- [raptorg multicast](https://medium.com/harmony-one/harmonys-networking-story-7a83fb6f13ed) <br >- [nkn message broadcast](https://github.com/harmony-one/bounties/issues/25) <br >-[Data Availability](https://medium.com/lazyledger/lazyledger-a-scalable-general-purpose-data-availability-layer-for-trust-minimized-sidechains-and-82d901963de9)

## :construction_worker: Contributing

Pull requests, issues, or other contributions from the community are encouraged!  You can not only add specific projects, but also potentially interesting fields/areas which are currently missing in the tech stack.

:heavy_exclamation_mark: All technologies listed above need to be open-source. Ideally, the links lead directly to the code.

_Note: You will need a GitHub account to suggest changes or open issues. If you do not have one, you may [sign up for free](https://github.com/join)._
