# Viem

Using Viem with Harmony protocol.

## Introduction

Viem is a TypeScript interface that provides low-level stateless primitives for interacting with Ethereum-compatible blockchains. It focuses on reliability, efficiency, and a developer-friendly experience. Harmony, being an Ethereum-compatible blockchain, can fully leverage Viem's capabilities. This allows developers to use Viem to interact with Harmony nodes seamlessly, benefiting from its performance optimizations and type-safe interface. By using Viem with Harmony, developers can build robust and efficient applications while enjoying a modern development experience.

## Setup Viem with Harmony

To get started with the Viem library, we first need to install it using the following command:

```
npm install viem
```

After installation, you can quickly set up and begin using the library with the following basic configuration:

```typescript
import { createPublicClient, http } from 'viem'
import { harmonyOne } from 'viem/chains'

// Create Viem instance
const client = createPublicClient({
  chain: harmonyOne,
  transport: http()
})

const blockNumber = await client.getBlockNumber()
console.log('blocknumber', blockNumber)
```

## Interacting with a Harmony Contract

Here's an example of how to interact with an HRC-20 token contract on the Harmony network using Viem. This example demonstrates how to efficiently retrieve multiple pieces of information in a single call using aggregation (via Multicall), which helps reduce network overhead and improve performance:

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

// Example: 1USDC on Harmony
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