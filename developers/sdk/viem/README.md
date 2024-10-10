# Viem

Using Viem with Harmony protocol.

## Introduction

Viem is a TypeScript interface that provides low-level stateless primitives for interacting with Ethereum-compatible blockchains. It focuses on reliability, efficiency, and a developer-friendly experience. As an Ethereum-compatible blockchain, Harmony can fully leverage Viem's capabilities. This allows developers to use Viem to interact with Harmony nodes seamlessly, benefiting from its performance optimizations and type-safe interface. By using Viem with Harmony, developers can build robust and efficient applications while enjoying a modern development experience.

## Setup Viem with Harmony

To get started with Viem, install it using the following command:

```
npm install viem
```

After installation, you can quickly set up and begin using the library with the following basic configuration:

```typescript
import { createPublicClient, http } from 'viem'
import { harmonyOne } from 'viem/chains'

const client = createPublicClient({
  chain: harmonyOne,
  transport: http()
})

const blockNumber = await client.getBlockNumber()
console.log('blocknumber', blockNumber)
```

Harmony Testnet is not supported by viem/chains. To connect to Testnet, you can create the chain using defineMethod:

```typescript
import { createPublicClient, http } from 'viem'
import { defineChain } from 'viem'

export const harmonyTestnet = defineChain({
  id: 1666700000,
  name: 'Harmony Testnet',
  nativeCurrency: {
    decimals: 18,
    name: 'ONE',
    symbol: 'ONE',
  },
  rpcUrls: {
    default: {
      http: ['https://api.s0.b.hmny.io'],
      webSocket: ['wss://ws.s0.b.hmny.io'],
    },
  },
  blockExplorers: {
    default: { name: 'Harmony Testnet Explorer', url: 'https://explorer.testnet.harmony.one/' },
  },
  testnet: true
})

const client = createPublicClient({
  chain: harmonyTestnet,
  transport: http()
})

```

## Interacting with a Harmony Contract

Here's an example of interacting with an HRC-20 token contract on the Harmony network using Viem. This example demonstrates how to efficiently retrieve multiple pieces of information in a single call using aggregation (via Multicall), which helps reduce network overhead and improve performance:

```typescript
import { createPublicClient, http } from 'viem'
import { getContract } from 'viem'
import { harmonyOne } from 'viem/chains'

const client = createPublicClient({
  batch: {
    multicall: true, 
  },
  chain: harmonyOne,
  transport: http(),
})

// 1USDC on Harmony
const address = '0x985458E523dB3d53125813eD68c274899e9DfAb4'  

const abi = parseAbi([
  'function balanceOf(address owner) view returns (uint256)',
  'function totalSupply() view returns (uint256)',
])

const contract = getContract({ address, abi, client })

const [totalSupply, balance] = await Promise.all([
  contract.read.totalSupply(),
  contract.read.balanceOf([address]),
])

console.log(`Total Supply: ${totalSupply}`)
console.log(`Balance of contract address: ${balance}`)
```

## Tutorials

In the case that you are interested in a more detailed step-by-step guide, you can go to our specific tutorials on using viem on a Harmony: &#x20;

{% content-ref url="mint-transaction.md" %}
[mint-transaction.md](mint-transaction.md)
{% endcontent-ref %}
