# Harmony Stack and Projects

The goal of this page is to provide an overview of the open-source Harmony Tech Stack.

This is a living document and we are relying on our community to contribute to it and help maintain it. Please feel free to make edits and additions via pull requests. We apologize if we missed your project!

* [About](harmony-stack.md#clipboard-about)
* [Layers of Harmony Stack](harmony-stack.md#bookmark_tabs-layers-of-polkadot-stack)
  * [User Interface](harmony-stack.md#iphone-user-interface)
  * [Tools, APIs and Languages](harmony-stack.md#wrench-tools-apis-and-languages)
  * [Bridges, Fiat Gateways, Exchanges](harmony-stack.md#memo-bridges-fiat-gateways-exchanges)
  * [Platform Modules](harmony-stack.md#nut_and_bolt-platform-modules)
  * [Crypto Projects](harmony-stack.md#link-crypto-projects)
  * [Signatures](harmony-stack.md#black_nib-signatures-and-cryptography)
  * [Core Harmony Protocol](harmony-stack.md#satellite-core)
* [Contributing](harmony-stack.md#construction_worker-contributing)

## About

The Harmony Tech Stack consists of the **open-source** technologies contributing to and relying on [Harmony](https://harmony.one). It is meant to be used for decentralized application \(Dapp\) development within numerous verticals including DeFi, Gaming, Provenance and many others not pictured below.

![Harmony Ecosystem](../.gitbook/assets/ecosystem_20.6.2021%20copy%20%281%29%20%281%29.png)

## Layers of Harmony Stack

In the below sections you can find a list of different layers of the Harmony Stack.

### User Interface

<table>
  <thead>
    <tr>
      <th style="text-align:left">Components</th>
      <th style="text-align:left">Existing projects</th>
      <th style="text-align:left">Potentially interesting projects</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Wallets</td>
      <td style="text-align:left"><a href="https://magic.link/">Magic</a>, <a href="https://sprout.sesameseed.org/">sprout</a>
      </td>
      <td style="text-align:left">
        <p>social recovery &amp; one-time-password authenticators for on-chain fund</p>
        <p></p>
        <p>basic income &amp; wealth from fixed-rate or high-yield investments</p>
        <p>
          <br />User-friendly Wallet based on open millions to self-custody assets &amp;
          collectibles without hardware, password or hack</p>
        <p>
          <br /><a href="https://github.com/hashmesan/harmony-totp">Composable Authentication</a> 
          <br
          /><a href="https://vitalik.ca/general/2021/01/11/recovery.html">Social onchain recovery</a> 
          <br
          /><a href="https://github.com/harmony-one/bounties/issues/35">EIP-2938 Account abstraction implementation</a> 
          <br
          /><a href="https://medium.com/@ronaldmannak/vivo-pay-a-zero-knowledge-payment-system-727997e4d25f">on-device privacy</a> 
          <br
          />Keyless Security
          <br />web3 integrations
          <br /><a href="https://github.com/harmony-one/bounties/issues/31">Harmony Argent Integration</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Browser Extensions</td>
      <td style="text-align:left"><a href="https://github.com/harmony-one/one-wallet">Harmony One Wallet</a>,
        <a
        href="https://mathwallet.org/web/harmony">Math Wallet</a>, <a href="https://metamask.io/">Metamask</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Mobile Wallets</td>
      <td style="text-align:left"><a href="https://frontierwallet.com/">Frontier wallet</a>, <a href="https://cobo.com/">Cobo Wallet</a>,
        <a
        href="https://mathwallet.org/">Math Wallet</a>, <a href="https://sevenb.io/">7b</a> , <a href="https://guarda.com/">Guarda</a>,
          <a
          href="https://edge.app/">Edge</a>, <a href="https://token.im/?locale=en-us">imtoken</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Hardware Wallets</td>
      <td style="text-align:left"><a href="https://www.ledger.com/">Ledger</a>, <a href="https://trezor.io/">Trezor</a>,
        <a
        href="https://safepal.io/">SafePal</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Block Explorers</td>
      <td style="text-align:left"><a href="https://explorer.harmony.one/">Harmony Explorer</a>
      </td>
      <td style="text-align:left"><a href="https://github.com/harmony-one/bounties/issues/37">Modular Explorer supporting HRC20 and HRC721</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Validator Dashboards</td>
      <td style="text-align:left"><a href="https://harmony.smartstake.io/">Smartstake</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Node Explorers</td>
      <td style="text-align:left"><a href="https://watchdog.hmny.io/report-mainnet">Watchdog</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Staking Rewards</td>
      <td style="text-align:left"><a href="https://harmony.smartstake.io/">Smartstake</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Analytics</td>
      <td style="text-align:left"><a href="https://docs.harmony.one/home/developers/tools/the-graph">The Graph</a>
      </td>
      <td style="text-align:left"><a href="https://github.com/harmony-one/bounties/issues/39">Dune Analytics Integration</a>
      </td>
    </tr>
  </tbody>
</table>

### Tools, APIs and Languages

| Components | Existing projects | Potentially interesting projects |
| :--- | :--- | :--- |
| Easy Smart Contract Development | [Truffle](https://www.trufflesuite.com/), [Remix](https://remix.ethereum.org/), [Hardhat](https://hardhat.org/), [Decentology](https://www.decentology.com/) |  |
| API |  | [API for Cross Chain Aggregation](https://medium.com/harmony-one/how-to-aggregate-cross-chain-liquidity-e2ef97ba2bf6) |
| Client Libraries |  |  |
| Runtime Security |  | Automated Runtime checking tools, economic audit simulator such as [gauntlet.network](https://gauntlet.network/) |

### Bridges, Fiat Gateways, Exchanges

| Components | Existing projects | Potentially interesting projects |
| :--- | :--- | :--- |
| Bridges | [Ethereum ](https://bridge.harmony.one/), [Binance](https://bridge.harmony.one/), [Polkadot - Edgeware](https://talk.harmony.one/t/everstake-polkadot-harmony-bridge/918) | [Trustless ONE BTC Bridge](https://docs.google.com/document/d/1Op1u9rbsR8sNwLblAYuFNONPCX5ODClVkOLt2mgBol0/edit#heading=h.wjz7s0uat2g5)   [Celo Optics Bridge](https://github.com/harmony-one/bounties/issues/33)  [Solana Wormhole Bridge](https://github.com/certusone/wormhole)  [Cosmos Gravity Bridge](https://github.com/cosmos/gravity-bridge)  [Terra Shuttle Bridge](https://github.com/terra-money/shuttle)   [DCRM Multichain Bridge](https://www.fusionite.info/post/dcrm-usecase-expanding-with-multichain-xyz) |
| Fiat Gatways | [Wyre](https://www.sendwyre.com/), [Swapzone](https://swapzone.io/), [Changelly](https://changelly.com/), [switchchain](https://www.switchain.com/), [swft](https://www.swft.pro/#/),  [SimpleSwap](https://simpleswap.io/), [simplex](https://www.simplex.com/), [transak](https://transak.com/) |  |
| Exchange Gateways | [Coinbase Rosetta](https://www.rosetta-api.org/) | [Rosetta API Extension](https://github.com/harmony-one/bounties/issues/3) |

### Platform Modules

| Components | Existing projects | Potentially interesting projects |
| :--- | :--- | :--- |
| Security | [Gnosis](https://gnosis.io/), [CertiK](https://www.certik.io/), [PeckShield](https://peckshield.com/en) | [coq verified execution](https://dl.acm.org/doi/abs/10.1145/1452044.1452049)  [information-flow: compositional reentrancy](https://www.cs.cornell.edu/andru/papers/oakland21/)  [session types: language design](https://harmony.one/design)  [smt: gas fee optimizer](https://twitter.com/stse/status/1328128280868708353) |
| Oracle | [Chainlink](https://chain.link/), [Band Protocol](https://bandprotocol.com/), [API3](https://api3.org/) |  |
| Privacy | [Dusk](https://dusk.network/), [Raze](https://www.raze.network/), [Webb Protocol](https://www.webb.tools/) |  |
| Governance/DAO | [Harmony Governance](https://gov.harmony.one/#/) |  |
| Cross Chain |  | [Cross Chain Arts and Collectibles](https://dappradar.com/blog/upland-and-blockchain-heroes-create-cross-chain-nft-cards) |
| Finality |  | [Madhi Zamani Instachain](http://mahdiz.com/?i=1)  [one second finality](https://github.com/harmony-one/bounties/issues/14) |
| Name Service | [crazy.one names](https://github.com/harmony-one/one-names) | [Name Service Key Address Resolution](https://medium.com/the-ethereum-name-service/ens-integration-spotlight-argent-bd8f9cf819f5) |

### Crypto Projects

| Components | Existing projects | Potentially interesting projects |
| :--- | :--- | :--- |
| DeFi | [Sushi](https://app.sushi.com/swap), [UMA Protocol](https://docs.umaproject.org/build-walkthrough/build-process), [daikiri finance](https://daikiri.finance/) | DEX with privacy and confidentiality features such as those found in a [dark pool](https://en.wikipedia.org/wiki/Dark_pool) |
| Automated Market Makers | [viperswap](https://viperswap.one/#/swap), [mochiswap](https://mochiswap.io/), [Reef](https://reef.finance/), [unifi](https://harmony.unifiprotocol.com/), [Injective Protocol](https://injectiveprotocol.com/), [JellySwap](https://jelly.market/), [SeeSwap](https://seeswap.one/), [OpenSwap](https://seeswap.one/), [LootSwap](https://lootswap.finance/), [swoop](https://swoop.exchange/) |  |
| Lending | [AAVE](https://aave.com/) |  |
| NFT | [Soccer Player](https://docs.harmony.one/home/developers/showcases/other-showcases#harmony-soccer-players), [Harmony One Punks](https://www.harmonypunks.one/) | [NFT as a wallet profile](https://www.christies.com/features/10-things-to-know-about-CryptoPunks-11569-1.aspx) |
| MarketPlaces | [daVinci](https://davinci.gallery/), [Travala](https://whitepaper.travala.com/), [utu](https://utu.io/protocol/), [Ript.io](https://ript.io/), [lma-art-gallery](https://lma-art-gallery.com/) | [ONE World: Geospatial NFT Marketplace](https://github.com/harmony-one/bounties/issues/48)  [Smart Markets for NFT'S](https://hbr.org/2007/10/the-art-of-designing-markets) |
| Fixed Rate Incomie |  | [Staking Derivatives](https://research.paradigm.xyz/staking)  [Fixed Rate Lending](https://twitter.com/stse/status/1378877524432707587)  [Interest Rate Markets](https://twitter.com/stse/status/1380695737131020289)  [Security Tranches](https://www.ledgerinsights.com/municipal-bonds-blockchain-tokenization-consensys-broker-acquisition/) |
| Cross chain DeFi |  | [Interest Free Stablecoin](https://twitter.com/stse/status/1386794075123163137)  [variable-rate lending](https://docs.google.com/document/d/1i6KoxDMKKCy5zBwXVkkNgAxTUFZjBIboMQAZPBY7bRs/edit#)  [Gas Fee Relay](https://github.com/harmony-one/bounties/issues/35)  [Privacy Mixer](https://www.notion.so/Harmony-EVM-Mixer-w-Bulletproofs-fdc691363fa946c2a24ec3141258bd31) |
| Staking | [Fuzz.fi](https://fuzz.fi/) |  |
| Staking Derivatives | [Stafi](https://stafi.io/) |  |
| Insurance | [DSLA Protocol](https://stacktical.com/) |  |
| Multichain | [ViteDex](https://www.vite.org/), [Jellyswap](https://jelly.market/), [Dogen Finance](https://dogen.finance/) |  |
| Lottery | [One Degen](https://onedegen.herokuapp.com/) |  |
| Token Issuance | [Token Jenny](https://tokenjenny.one/) |  |
| Charity | [Moonity](https://moonity.one/home#about) |  |
| Real Estate | [Monopoly](https://mply.org/) |  |
| Gaming | [Nano Royale](https://nanoroyale.com/), [freyala](https://www.freyala.com), [defi kingdoms](https://defikingdoms.com), [geriatrics gaming](https://geriatricsgaming.com) |  |
| Gambling | [lootblocks](https://lootblocks.one) |  |
| Multisig App Store |  | gnosis safe: multisig app store |
| Payroll |  | [Decentralized Payroll Management for DAO's](https://medium.com/iearn/decentralized-payroll-management-for-daos-b2252160c543) |
| Identity/DID | [Hypersign Identity](https://hypersign.id) |  |
| Social Networking |  | [Social Referral](https://medium.com/terra-money/introducing-buzlink-scaling-social-referrals-5e08c2c65e8e) |
| Governance/DAO |  |  |
| Other | [Knit Finance](https://knit.finance/#token-economy), [MakiMoon](https://maki.one/why), [harmony validators](https://www.harmonyvalidators.com/) |  |

### Signatures and Cryptography

| Components | Existing projects | Potentially interesting projects |
| :--- | :--- | :--- |
| Cryptography |  | [evmcurve bls12-381](https://notes.ethereum.org/@poemm/evm384-update5#Gas-Estimates-for-BLS12-381-Operations) |
| Key Value Commitments |  | [Key Value Commitments](https://eprint.iacr.org/2020/1161) |
| BulletProof |  | [EVM Mixer with Bulletproofs](https://www.notion.so/Harmony-EVM-Mixer-w-Bulletproofs-fdc691363fa946c2a24ec3141258bd31) |
| Privacy |  | [poseidon hash precompile using curve25519](https://blog.harmony.one/privacy-on-harmony-powered-by-webb/) |
| Light Clients |  | [superlight client, bootstrap without header sync](https://twitter.com/stse/status/1395033039168688134)  [lightclient: epoch synch](https://medium.com/harmony-one/dusk-network-and-harmony-partner-to-build-towards-the-first-industry-grade-zero-knowledge-proof-c7b16f740a84) |
| Zero Knowledge |  | [zksnark: plonk](https://medium.com/harmony-one/dusk-network-and-harmony-partner-to-build-towards-the-first-industry-grade-zero-knowledge-proof-c7b16f740a84) |
| ethereum rollups |  | [zero knowledge proofs](https://zksync.io/)  [zk porter l2 scaling](https://medium.com/matter-labs/zkporter-a-breakthrough-in-l2-scaling-ed5e48842fbf)  [zk-zk-rollup](https://medium.com/aztec-protocol/aztecs-zk-zk-rollup-looking-behind-the-cryptocurtain-2b8af1fca619)  [l2 for private transactions](https://zkopru.network/) |

### Core Harmony Protocol

| Components | Existing projects | Potentially interesting projects |
| :--- | :--- | :--- |
| Networking |  | [quic data transport](https://medium.com/harmony-one/harmonys-networking-story-7a83fb6f13ed)  [hipv2 node identity](https://medium.com/harmony-one/harmonys-networking-story-7a83fb6f13ed)  [raptorg multicast](https://medium.com/harmony-one/harmonys-networking-story-7a83fb6f13ed)  [nkn message broadcast](https://github.com/harmony-one/bounties/issues/25)  [Data Availability](https://medium.com/lazyledger/lazyledger-a-scalable-general-purpose-data-availability-layer-for-trust-minimized-sidechains-and-82d901963de9) |

## Contributing

Pull requests, issues, or other contributions from the community are encouraged! You can not only add specific projects, but also potentially interesting fields/areas which are currently missing in the tech stack.

:heavy\_exclamation\_mark: All technologies listed above need to be open-source. Ideally, the links lead directly to the code.

_Note: You will need a GitHub account to suggest changes or open issues. If you do not have one, you may_ [_sign up for free_](https://github.com/join)_._

