# Hardhat

A quick guide on how to verify your contracts on Harmony with Hardhat.

## 1. Install @nomiclabs/hardhat-etherscan

Ensure you have a version >= 3.1.0 of @nomiclabs/hardhat-etherscan installed

```
npm i @nomiclabs/hardhat-etherscan
```

## 2. Add Harmony Networks to hardhat.config.ts

```ts
const config: HardhatUserConfig = {
    networks: {
        harmonyDevnet: {
            url: `https://api.s0.ps.hmny.io`,
            accounts: [`0x${HARMONY_PRIVATE_KEY}`]
        },
        harmonyTestnet: {
            url: `https://api.s0.b.hmny.io`,
            accounts: [`0x${HARMONY_PRIVATE_KEY}`]
        },
        harmonyMainnet: {
            url: `https://api.harmony.one`,
            accounts: [`0x${HARMONY_PRIVATE_KEY}`]
        }
    }
};
```

## 3. Add api keys to hardhat.config.ts

Any string can be used for your api key.

```ts
const config: HardhatUserConfig = {
  etherscan: {
    apiKey: {
      harmony: "your API key",
      harmonyDevnet: "your API key"
    }
  }
};
```

## 4. (Devnet Only) Add devnet under custom chains in hardhat.config.ts

```ts
const config: HardhatUserConfig = {
    etherscan: {
        customChains: [
            {
                network: "harmonyDevnet",
                chainId: 1666900000,
                urls: {
                    apiURL: "https://ctrver.t.hmny.io/verify?network=devnet",
                    browserURL: "https://explorer.ps.hmny.io/"
                }
            }
        ]
    }
};
```

## 5. Run npx hardhat verify

```
npx hardhat verify --network <network name> <deployed contract address> "Constructor Argument 1" "Constructor Argument 2"
```

## Errors

Please report any issues you run into here: https://github.com/harmony-one/contract-verification-service.