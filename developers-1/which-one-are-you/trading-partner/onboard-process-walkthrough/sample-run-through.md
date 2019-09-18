# Sample Run  Through

1. Installing the CLI
2. Create an Account \(Binance Account\)

```text
Johns-MacBook-Pro:go-sdk johnwhitton$ ./hmy keys add binance_foundation
**Important** write this seed phrase in a safe place, it is the only way to recover your account if you ever forget your password

behind grow afford mix job switch hand problem submit mistake sound pyramid thunder pink canvas fence check want brief between pizza coffee immense collect
Johns-MacBook-Pro:go-sdk johnwhitton$ ./hmy keys list
NAME                                            ADDRESS

binance_foundation                                  one1502q7438y68m4qtqqetm99hez8ru5h4yzegp9y
```

```text
Johns-MacBook-Pro:go-sdk johnwhitton$ ./hmy keys add harmony_foundation --recover
Enter mnemonic to recover keys from
urge clog right example dish drill card maximum mix bachelor section select
Johns-MacBook-Pro:go-sdk johnwhitton$ ./hmy keys list
NAME                                            ADDRESS

binance_foundation                                  one1502q7438y68m4qtqqetm99hez8ru5h4yzegp9y
harmony_foundation                                  one1k2u4hl60jyzev8f39r0275hggjx99ayr8nzdtw
```

```text
Johns-MacBook-Pro:go-sdk johnwhitton$ ./hmy --node="https://api.s1.b.hmny.io/" --pretty balance one1k2u4hl60jyzev8f39r0275hggjx99ayr8nzdtw
[
  {
    "shard": 0,
    "amount": 0.0000
  },
  {
    "shard": 1,
    "amount": 130.0000
  }
]
```

1. Fund Binance Account

```text
Johns-MacBook-Pro:go-sdk johnwhitton$ ./hmy transfer --from one1k2u4hl60jyzev8f39r0275hggjx99ayr8nzdtw --to one1502q7438y68m4qtqqetm99hez8ru5h4yzegp9y --amount 30 --from-shard 1 --to-shard 1 --node="https://api.s1.b.hmny.io/"
{"transaction-receipt":"0x5b0e4f2812db732e83f97b7d11a63b9f94261819805cf457663018b8d41b8872"}
Johns-MacBook-Pro:go-sdk johnwhitton$ ./hmy --node="https://api.s1.b.hmny.io" --pretty blockchain transaction-by-receipt  0x5b0e4f2812db732e83f97b7d11a63b9f94261819805cf457663018b8d41b8872
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0x68186dbe9faa2989c2a3c626ad9332391acbee2f1fa1e97193d9124746dfe446",
    "blockNumber": "0x4bc0",
    "contractAddress": null,
    "cumulativeGasUsed": "0x5208",
    "from": "0xb2b95bff4f9105961d3128deaf52e8448c52f483",
    "gasUsed": "0x5208",
    "logs": [],
    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "shardID": 1,
    "status": "0x1",
    "to": "0xa3d40f5627268fba81600657b296f911c7ca5ea4",
    "transactionHash": "0x5b0e4f2812db732e83f97b7d11a63b9f94261819805cf457663018b8d41b8872",
    "transactionIndex": "0x0"
  }
```

1. Create Alices Account
2. Fund Alices Account
3. Alice Sells Some Ones
4. Alice Sends some ONE'S to Bob

