# Table of contents

* [Introduction](README.md)

## Harmony Networks

* [Overview](harmony-networks/harmony-network-overview/README.md)
  * [Mainnet](harmony-networks/harmony-network-overview/mainnet.md)
  * [Testnet/Pangaea](harmony-networks/harmony-network-overview/testnet-pangaea.md)
* [Wallet guides](harmony-networks/wallet-guides.md)

## Wallet guides

* [Harmony CLI](wallet-guides/harmony-cli/README.md)
  * [Download and setup](wallet-guides/harmony-cli/download-setup.md)
  * [Creating new wallet/importing wallet](wallet-guides/harmony-cli/create-import-wallet.md)
  * [Sending transactions](wallet-guides/harmony-cli/send-tx.md)
  * [Querying balance](wallet-guides/harmony-cli/querying-balance.md)
  * [Querying the blockchain](wallet-guides/harmony-cli/querying-the-blockchain.md)
  * [Key management](wallet-guides/harmony-cli/key-management.md)
  * [Other CLI reference](wallet-guides/harmony-cli/other-cli-reference.md)
* [Trustwallet](wallet-guides/trustwallet.md)
* [Mathwallet](wallet-guides/mathwallet.md)
* [Ledger](wallet-guides/ledger.md)
* [Safepal](wallet-guides/safepal.md)

## Developers

* [Which ONE are you?](developers/which-one-are-you.md)
* [Smart Contract Developer](developers/hrc/README.md)
  * [Smart Contract Development using Truffle](developers/hrc/smart-contract-development-using-truffle.md)
  * [Sample Files](developers/hrc/sample-files.md)
* [Trading Partner](developers/trading-partner/README.md)
  * [Partner on-boarding reference material](developers/trading-partner/on-boarding-process/README.md)
    * [Connecting to Harmony \(Running a node\)](developers/trading-partner/on-boarding-process/connecting-to-harmony-running-a-node.md)
  * [Onboard Process Walkthrough](developers/trading-partner/onboard-process-walkthrough.md)

## API Developers Guide <a id="api"></a>

* [Introduction](api/overview/README.md)
  * [Sample Code](api/overview/sample-code.md)
  * [Sample nodejs CLI Application](api/overview/sample-nodejs-cli-application.md)
* [Methods](api/methods/README.md)
  * [Account Methods](api/methods/account-methods/README.md)
    * [hmy\_getTransactionCount](api/methods/account-methods/hmy_gettransactioncount.md)
    * [hmy\_getBalance](api/methods/account-methods/hmy_getbalance.md)
    * [address](api/methods/account-methods/getexploreraddress.md)
  * [Transaction Related Methods](api/methods/transaction-related-methods/README.md)
    * [hmy\_sendRawStakingTransaction](api/methods/transaction-related-methods/hmy_sendrawstakingtransaction.md)
    * [hmy\_getTransactionsHistory](api/methods/transaction-related-methods/hmy_gettransactionshistory.md)
    * [hmy\_sendRawTransaction](api/methods/transaction-related-methods/hmy_sendrawtransaction.md)
    * [hmy\_getTransactionReceipt](api/methods/transaction-related-methods/hmy_gettransactionreceipt.md)
    * [hmy\_getBlockTransactionCountByHash](api/methods/transaction-related-methods/hmy_getblocktransactioncountbyhash.md)
    * [hmy\_getBlockTransactionCountByNumber](api/methods/transaction-related-methods/hmy_getblocktransactioncountbynumber.md)
    * [hmy\_getTransactionByHash](api/methods/transaction-related-methods/hmy_gettransactionbyhash.md)
    * [hmy\_getTransactionByBlockNumberAndIndex](api/methods/transaction-related-methods/hmy_gettransactionbyblocknumberandindex.md)
    * [hmy\_getTransactionByBlockHashAndIndex](api/methods/transaction-related-methods/hmy_gettransactionbyblockhashandindex.md)
    * [hmy\_getBlockByNumber](api/methods/transaction-related-methods/hmy_getblockbynumber.md)
    * [hmy\_getBlockByHash](api/methods/transaction-related-methods/hmy_getblockbyhash.md)
    * [hmy\_getBlocks](api/methods/transaction-related-methods/hmy_getblocks.md)
    * [tx](api/methods/transaction-related-methods/getexplorerblocks.md)
  * [Contract Related Methods](api/methods/contract-related-methods/README.md)
    * [hmy\_getCode](api/methods/contract-related-methods/hmy_getcode.md)
  * [Protocol Related Methods](api/methods/blockchain-related-methods/README.md)
    * [hmy\_getShardingStructure](api/methods/blockchain-related-methods/hmy_getshardingstructure.md)
    * [hmy\_blockNumber](api/methods/blockchain-related-methods/hmy_blocknumber.md)
    * [hmy\_syncing](api/methods/blockchain-related-methods/hmy_syncing.md)
    * [hmy\_gasPrice](api/methods/blockchain-related-methods/hmy_gasprice.md)
    * [net\_peerCount](api/methods/blockchain-related-methods/net_peercount.md)
    * [committee](api/methods/blockchain-related-methods/getexplorertransaction.md)
    * [blocks](api/methods/blockchain-related-methods/untitled.md)
    * [shard](api/methods/blockchain-related-methods/getexplorershard.md)
    * [node-count](api/methods/blockchain-related-methods/getexplorernodecount.md)
    * [hmy\_getEpoch](api/methods/blockchain-related-methods/hmy_getepoch.md)
    * [hmy\_getLeader](api/methods/blockchain-related-methods/hmy_getleader.md)
  * [Staking Related Methods](api/methods/staking-related-methods/README.md)
    * [hmy\_getDelegatorsInformation](api/methods/staking-related-methods/hmy_getdelegatorsinformation.md)
    * [hmy\_getValidatorStakingAddress](api/methods/staking-related-methods/hmy_getvalidatorstakingaddress.md)
    * [hmy\_getValidators](api/methods/staking-related-methods/hmy_getvalidators.md)
    * [hmy\_getStake](api/methods/staking-related-methods/hmy_getstake.md)
    * [hmy\_getSignedBlocks](api/methods/staking-related-methods/hmy_getsignedblocks.md)
    * [hmy\_isBlockSigner](api/methods/staking-related-methods/hmy_isblocksigner.md)
    * [hmy\_getBlockSigners](api/methods/staking-related-methods/hmy_getblocksigners.md)
    * [hmy\_getValidatorStakingWithDelegation](api/methods/staking-related-methods/hmy_getvalidatorstakingwithdelegation.md)

## Command Line Interface

* [Using the Harmony CLI tool](command-line-interface/using-the-harmony-cli-tool/README.md)
  * [Query Balances](command-line-interface/using-the-harmony-cli-tool/query-balances.md)
  * [Download and installation](command-line-interface/using-the-harmony-cli-tool/download-and-installation.md)
  * [Key management](command-line-interface/using-the-harmony-cli-tool/key-management.md)
  * [Creating, sending transactions](command-line-interface/using-the-harmony-cli-tool/creating-sending-transactions.md)
  * [Querying the blockchain](command-line-interface/using-the-harmony-cli-tool/querying-the-blockchain.md)
  * [Full CLI Reference](command-line-interface/using-the-harmony-cli-tool/full-cli-reference.md)

## Open Staking Guide

* [Using Ledger For Sending Tokens & Staking](open-staking-guide/ledger-staking-guide.md)

## Archived/Obsolete

* [Harmony Docs Archives](archived-obsolete/harmony-docs-archives/README.md)
  * [Testnet](archived-obsolete/harmony-docs-archives/betanet/README.md)
    * [Test Accounts](archived-obsolete/harmony-docs-archives/betanet/developer-1.md)
  * [Devcon5](archived-obsolete/harmony-docs-archives/devcon5.md)
  * [Non-validating Nodes](archived-obsolete/harmony-docs-archives/non-validating-nodes.md)

## USER GUIDE

* [Wallet Overview](user-guide/wallets/README.md)
  * [Ledger Nano S](user-guide/wallets/ledger-nano-s/README.md)
    * [Install Harmony App for Ledger Nano S](user-guide/wallets/ledger-nano-s/install-harmony-app-for-ledger-nano-s.md)
    * [Ledger Nano S Hardware Wallet Guide](user-guide/wallets/ledger-nano-s/ledger-nano-s-hardware-wallet-guide-1.md)
    * [Ledger Nano S Firmware Usage Manual](user-guide/wallets/ledger-nano-s/ledger-nano-s-firmware-usage-manual.md)
  * [Math Wallet](user-guide/wallets/mathwallet/README.md)
    * [Setup](user-guide/wallets/mathwallet/setup.md)
    * [How to Send Transactions](user-guide/wallets/mathwallet/making-transactions.md)
  * [SafePal](user-guide/wallets/safepal.md)

