# Using Brownie

1\. Install brownie via pipx

```
pipx install eth-brownie
```

2\. Modify `network-config.yaml` to add Harmony under live networks.

```
  - name: Harmony
    networks:
      - name: Harmony Mainnet
        chainid: 1666600000
        id: hmainnet
        host: https://api.harmony.one
        explorer: https://explorer.harmony.one/
      - name: Harmony Testnet
        chainid: 1666700000
        id: htestnet
        host: https://api.s0.b.hmny.io
        explorer:  https://explorer.pops.one/
```

3\. Create a folder and initialize brownie within

```
mkdir myProject
cd myProject
brownie init
```

4\. Open console to deploy and test contracts on Harmony network.

```
brownie console --network htestnet
```
Brownie Docs https://eth-brownie.readthedocs.io/
