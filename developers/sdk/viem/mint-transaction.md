# Minting Tokens with Viem on Harmony

Minting is a crucial operation in many blockchain applications, allowing the creation of new tokens. This guide demonstrates how to implement a minting function using Viem, a TypeScript interface for Ethereum, on the Harmony network.

## Basic Minting Operation

First, let's look at a basic implementation of a minting component:

```typescript
import { createWalletClient, custom, parseAbi, Address } from 'viem'
import { parseUnits } from 'viem/utils'
import { useAccount } from 'wagmi'
import { harmonyTestnet } from '@/lib/chains'
import { TOKEN_DECIMALS, TOKEN_CONTRACT_ADDRESS } from '@/lib/constants'

const walletClient = createWalletClient({
  chain: harmonyTestnet,
  transport: custom(window.ethereum)
})

export const MintingComponent: React.FC = () => {
  const [status, setStatus] = useState<string>('')
  const [amount, setAmount] = useState<string>('1')

  const account = useAccount()

  const handleMint = async () => {
    try {
      const address = account.address
      const amountToMint = parseUnits(amount, TOKEN_DECIMALS)

      const hash = await walletClient.writeContract({
        address: TOKEN_CONTRACT_ADDRESS,
        abi,
        functionName: 'mint',
        args: [address as Address, amountToMint],
        account: address as Address
      })

      setStatus(`Minting successful! Transaction hash: ${hash}`)

    } catch (error) {
      console.error('Error during minting:', error)
      setStatus(`Minting failed: ${error.message}`)
    }
  }

  return (
    // ... component JSX
  )
}
```

In this example, we create a wallet client using Viem's `createWalletClient` function outside the component to avoid recreating it on each render. We then use the `writeContract` method to send a transaction to the token contract's `mint` function.

## Simulating the Transaction

Before executing a transaction that could potentially cost gas, it's a good practice to simulate it first. Viem provides the `simulateContract` function for this purpose. Here's an enhanced version of the minting component that includes transaction simulation:

```typescript
import { createWalletClient, createPublicClient, http, custom, parseAbi, Address } from 'viem'
import { parseUnits } from 'viem/utils'
import { useAccount } from 'wagmi'
import { harmonyTestnet } from '@/lib/chains'
import { TOKEN_DECIMALS, TOKEN_CONTRACT_ADDRESS } from '@/lib/constants'

const walletClient = createWalletClient({
  chain: harmonyTestnet,
  transport: custom(window.ethereum)
})

const publicClient = createPublicClient({
  chain: harmonyTestnet,
  transport: http()
})

const MintingComponent: React.FC = () => {
  const [status, setStatus] = useState<string>('')
  const [amount, setAmount] = useState<string>('1')

  const account = useAccount()

  const handleMint = async () => {
    try {
      const address = account.address
      const amountToMint = parseUnits(amount, TOKEN_DECIMALS)
      
      // Simulate the transaction first
      const { request } = await publicClient.simulateContract({
        address: TOKEN_CONTRACT_ADDRESS,
        abi,
        functionName: 'mint',
        args: [address, amountToMint],
        account: address
      })

      // If simulation is successful, execute the actual transaction
      if (request) {
        const hash = await walletClient.writeContract(request)
        console.log('Minting transaction hash:', hash)
        setStatus(`Minting successful! Transaction hash: ${hash}`)
      } else {
        setStatus('Simulation failed. Unable to proceed with minting.')
      }
    
    } catch (error) {
      console.error('Error during minting:', error)
      setStatus(`Minting failed: ${error.message}`)
    }
  }

  return (
    // ... component JSX
  )
}
```

This implementation uses `simulateContract` to validate the transaction before execution, preventing unnecessary gas costs. It utilizes both `walletClient` for transactions and `publicClient` for simulations, defined outside the component for efficiency. The `address` and `amountToMint` are calculated inside the `handleMint` function to ensure the latest values are used.

