# About

### Key points

* First trustless and decentralized bitcoin bridge to EVM chain
* Based on [XCLAIM](https://eprint.iacr.org/2018/643) protocol peer-reviewed research paper by [Interlay](https://interlay.io) co-founders
* Decentralized vaults that custodies user bitcoins are over collateralized to prevent any malicious behaviors by vaults
* Secured by Chainlink oracle [price feeds](https://docs.harmony.one/home/developers/tools/oracles/chainlink)

### Bridge Actors

* Vaults
  * Receive and hold user bitcoins to allow them create wrapped bitcoins (1BTC)
* Users
  * Users can request to get issued with wrapped BTC for the BTC that they lock with vaults. Users can request to redeem their BTC by burning the wrapped BTC and unlocking their BTC from vaults
* Relayer
  * Relay Bitcoin block headers to Relay smart contract on Harmony

### Bridge Flows

TBD

### Bridge Fees

Issue/Redeem: 0.5%
