# Harmony Ethers.js Wrapper

Repo: [https://github.com/harmony-one/harmony-ethers-sdk](https://github.com/harmony-one/harmony-ethers-sdk)

### Example: How to use provider to query Harmony chain

```
import {
  Block,
  BlockWithTransactions,
  CXTransactionReceipt,
  StakingTransactionResponse,
  TransactionReceipt,
  TransactionResponse,
} from "../src/types";
import { ApiHarmonyProvider } from "../src/provider";

// provider auto detects shard
const provider = new ApiHarmonyProvider("https://api.s0.b.hmny.io");
// to get block with harmony properties
const block: Block = await provider.getBlock(blockNumber || blockHash);
// to get block with transactions including staking transactions
const blockWithTransaction: BlockWithTransactions = await provider.getBlockWithTransactions(blockNumber || blockHash);

// get transaction / cx transaction
const tx: TransactionResponse = provider.getTransaction(txHash);
// get staking transaction
const sTx: StakingTransactionResponse = provider.getStakingTransaction(txHash);

// to get staking transaction recipt
const txReceipt: TransactionReceipt = provider.getTransactionReceipt(txHash);

// to get Cross Shard Receipt
const cTxReceipt: CXTransactionReceipt = provider.getCXTransactionReceipt(txHash);
```
