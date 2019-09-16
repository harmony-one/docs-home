# Table of contents

* [Harmony Developers Guide](README.md)

## Harmony Networks

* [Harmony Network Overview](harmony-networks/harmony-network-overview/README.md)
  * [Mainnet](harmony-networks/harmony-network-overview/mainnet.md)
  * [Pangea](harmony-networks/harmony-network-overview/pangea.md)
  * [Betanet](harmony-networks/harmony-network-overview/betanet/README.md)
    * [Test Accounts](harmony-networks/harmony-network-overview/betanet/developer-1.md)
* [Connecting to the Harmony Network](harmony-networks/connecting-to-the-harmony-network/README.md)
  * [Non-validating Nodes](harmony-networks/connecting-to-the-harmony-network/non-validating-nodes.md)

## Developers <a id="developers-1"></a>

* [WHICH ONE ARE YOU](developers-1/which-one-are-you/README.md)
  * [DApp Developer](developers-1/which-one-are-you/developer.md)
  * [Smart Contract Devel](developers-1/which-one-are-you/smart-contract-devel.md)
  * [Wallet Creator](developers-1/which-one-are-you/wallet-creator.md)
  * [Explorer Creator](developers-1/which-one-are-you/explorer-creator.md)
  * [Trading Partner](developers-1/which-one-are-you/trading-partner/README.md)
    * [Partner on-boarding process](developers-1/which-one-are-you/trading-partner/on-boarding-process/README.md)
      * [Pre-requisites](developers-1/which-one-are-you/trading-partner/on-boarding-process/pre-requisites.md)
      * [Connecting to Harmony \(Running a node\)](developers-1/which-one-are-you/trading-partner/on-boarding-process/connecting-to-harmony-running-a-node.md)
      * [Managing Accounts](developers-1/which-one-are-you/trading-partner/on-boarding-process/managing-accounts/README.md)
        * [KYC Process](developers-1/which-one-are-you/trading-partner/on-boarding-process/managing-accounts/kyc-process.md)
      * [Token Swap Process](developers-1/which-one-are-you/trading-partner/on-boarding-process/token-swap-process.md)
      * [Trading Process](developers-1/which-one-are-you/trading-partner/on-boarding-process/trading-process.md)
      * [BEP2 to ERC20 Swap](developers-1/which-one-are-you/trading-partner/on-boarding-process/bep2-to-erc20-swap.md)
    * [Onboard Process Walkthrough](developers-1/which-one-are-you/trading-partner/onboard-process-walkthrough/README.md)
      * [Sample Run  Through](developers-1/which-one-are-you/trading-partner/onboard-process-walkthrough/sample-run-through.md)
    * [Reference Material](developers-1/which-one-are-you/trading-partner/reference-material.md)
  * [Harmony Validator](developers-1/which-one-are-you/harmony-validator/README.md)
    * [Validator Overview](developers-1/which-one-are-you/harmony-validator/validator-overview.md)
    * [Pangaea](developers-1/which-one-are-you/harmony-validator/pangaea.md)
    * [Foundational Nodes](developers-1/which-one-are-you/harmony-validator/foundational-nodes.md)

## Developer Tools <a id="devtools"></a>

* [Local Harmony Blockchain](devtools/local-harmony-blockchain/README.md)
  * [Harmony Local Node Configuration](devtools/local-harmony-blockchain/harmony-local-node-configuration.md)
  * [Updating your codebase to latest](devtools/local-harmony-blockchain/updating-your-codebase-to-latest.md)
  * [Running a Local Node](devtools/local-harmony-blockchain/running-a-local-node.md)
  * [Account Information](devtools/local-harmony-blockchain/account-information.md)
  * [Funding your wallet](devtools/local-harmony-blockchain/funding-your-wallet.md)
  * [Transferring Funds](devtools/local-harmony-blockchain/transferring-funds.md)
* [Smart Contract Development](devtools/smart-contract-development/README.md)
  * [Smart Contracts development using Truffle](devtools/smart-contract-development/writing-smart-contracts/README.md)
    * [truffle-config.js](devtools/smart-contract-development/writing-smart-contracts/untitled.md)

## API Developers Guide

* [Introduction](api-developers-guide/overview/README.md)
  * [Sample Code](api-developers-guide/overview/sample-code.md)
  * [Sample nodejs CLI Application](api-developers-guide/overview/sample-nodejs-cli-application.md)
  * [Account Methods](api-developers-guide/overview/account-methods/README.md)
    * [hmy\_getTransactionCount](api-developers-guide/overview/account-methods/hmy_gettransactioncount.md)
    * [hmy\_getBalance](api-developers-guide/overview/account-methods/hmy_getbalance.md)
    * [address](api-developers-guide/overview/account-methods/getexploreraddress.md)
  * [Transaction Related Methods](api-developers-guide/overview/transaction-related-methods/README.md)
    * [hmy\_sendRawTransaction](api-developers-guide/overview/transaction-related-methods/hmy_sendrawtransaction.md)
    * [hmy\_getTransactionReceipt](api-developers-guide/overview/transaction-related-methods/hmy_gettransactionreceipt.md)
    * [hmy\_getBlockTransactionCountByHash](api-developers-guide/overview/transaction-related-methods/hmy_getblocktransactioncountbyhash.md)
    * [hmy\_getBlockTransactionCountByNumber](api-developers-guide/overview/transaction-related-methods/hmy_getblocktransactioncountbynumber.md)
    * [hmy\_getTransactionByHash](api-developers-guide/overview/transaction-related-methods/hmy_gettransactionbyhash.md)
    * [hmy\_getTransactionByBlockNumberAndIndex](api-developers-guide/overview/transaction-related-methods/hmy_gettransactionbyblocknumberandindex.md)
    * [hmy\_getTransactionByBlockHashAndIndex](api-developers-guide/overview/transaction-related-methods/hmy_gettransactionbyblockhashandindex.md)
    * [hmy\_getBlockByNumber](api-developers-guide/overview/transaction-related-methods/hmy_getblockbynumber.md)
    * [hmy\_getBlockByHash](api-developers-guide/overview/transaction-related-methods/hmy_getblockbyhash.md)
    * [tx](api-developers-guide/overview/transaction-related-methods/getexplorerblocks.md)
  * [Contract Related Methods](api-developers-guide/overview/contract-related-methods/README.md)
    * [hmy\_getCode](api-developers-guide/overview/contract-related-methods/hmy_getcode.md)
    * [hmy\_call](api-developers-guide/overview/contract-related-methods/hmy_call.md)
  * [Protocol Related Methods](api-developers-guide/overview/blockchain-related-methods/README.md)
    * [hmy\_blockNumber](api-developers-guide/overview/blockchain-related-methods/hmy_blocknumber.md)
    * [net\_peerCount](api-developers-guide/overview/blockchain-related-methods/net_peercount.md)
    * [hmy\_syncing](api-developers-guide/overview/blockchain-related-methods/hmy_syncing.md)
    * [Template](api-developers-guide/overview/blockchain-related-methods/template.md)
    * [hmy\_estimateGas](api-developers-guide/overview/blockchain-related-methods/hmy_estimategas.md)
    * [hmy\_gasPrice](api-developers-guide/overview/blockchain-related-methods/hmy_gasprice.md)
    * [committee](api-developers-guide/overview/blockchain-related-methods/getexplorertransaction.md)
    * [blocks](api-developers-guide/overview/blockchain-related-methods/untitled.md)
    * [shard](api-developers-guide/overview/blockchain-related-methods/getexplorershard.md)
    * [node-count](api-developers-guide/overview/blockchain-related-methods/getexplorernodecount.md)

## Command Line Interface

* [Using the Harmony CLI tool](command-line-interface/using-the-harmony-cli-tool/README.md)
  * [Account](command-line-interface/using-the-harmony-cli-tool/account.md)
  * [Blockchain](command-line-interface/using-the-harmony-cli-tool/blockchain.md)
  * [Transfer](command-line-interface/using-the-harmony-cli-tool/transfer.md)
  * [Keys](command-line-interface/using-the-harmony-cli-tool/keys.md)

