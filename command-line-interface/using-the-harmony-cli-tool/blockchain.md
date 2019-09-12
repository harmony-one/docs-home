---
description: Interacting with the Harmony blockchain
---

# Blockchain

## Available Actions

{% hint style="info" %}
The `-p` option pretty-prints JSON output for readability. Omitting this option prints JSON output on a single line.
{% endhint %}

### Get Harmony blockchain block by block number

```bash
$ ./hmy_cli -p blockchain block-by-number 0xA7
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "difficulty": 0,
    "extraData": "0x",
    "gasLimit": "0x54a1b1",
    "gasUsed": "0x0",
    "hash": "0x39c53d79404803e5c20da54463d9b3314baca7f4e9204197cfcafeae999c1c95",
    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "miner": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016",
    "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "nonce": 0,
    "number": "0xa7",
    "parentHash": "0xc8e1bbdd21d39b342914ca99786187cf63895ee2fa2d988dd50643e79629db42",
    "receiptsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
    "size": "0x548",
    "stateRoot": "0xfcc55f32f3cb66467d9d9f29f2301443779c40fd83fabf72642c93928eaadc7c",
    "timestamp": "0x5d72e587",
    "transactions": [],
    "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
    "uncles": []
  }
}
```

### Get version of the Harmony Protocol

```bash
$ ./hmy_cli -p blockchain protocol-version
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": "0x1"
}
```

### Get transaction by hash

```bash
$ ./hmy_cli -p blockchain transaction-by-hash 0xd957f79fb2548221c7316a4e2b0cb30c93edc64b5f837a77baeb2e2d1e46b804
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0x047ed5421ab89e881b1af307d15ca626d5bccde41afa40b6c02b68d060083f3a",
    "blockNumber": "0xc7",
    "from": "0x13e88a505dd804971410ac5538c504c376464227",
    "gas": "0x5208",
    "gasPrice": "0x0",
    "hash": "0xd957f79fb2548221c7316a4e2b0cb30c93edc64b5f837a77baeb2e2d1e46b804",
    "input": "0x",
    "nonce": "0x0",
    "r": "0xe00b21afaddfb08899772de61f3596c9d92c22bf243254725c829cc73a1da14c",
    "s": "0x6cc4799ffb922a347c4748753247efc882b75cffcc77c21c30090ceec28e6d7a",
    "to": "0xe1217e2a4861dd5d50983dad32474bbfd6a7333f",
    "transactionIndex": "0x0",
    "v": "0x1c",
    "value": "0x56bc75e2d63100000"
  }
}
```

### Get transaction by receipt

```bash
$ hc blockchain transaction-by-receipt 0x0c4cf02b90670fc7111de02de12ddb8af03120ca2b196ed3ad945692bf18fd27
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0xf32f0fe01a749472c07f449989a99efbecd3f7a964defe7c53fb11641b50c17e",
    "blockNumber": "0x6f8",
    "contractAddress": null,
    "cumulativeGasUsed": "0x5208",
    "from": "0x13e88a505dd804971410ac5538c504c376464227",
    "gasUsed": "0x5208",
    "logs": [],
    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "root": "0x6529054bd44f6f81ff151956cb795cf605c8913609ce24044becdab4bfa166fc",
    "shardID": 0,
    "to": "0xe1217e2a4861dd5d50983dad32474bbfd6a7333f",
    "transactionHash": "0x0c4cf02b90670fc7111de02de12ddb8af03120ca2b196ed3ad945692bf18fd27",
    "transactionIndex": "0x0"
  }
}
```

### Get a transaction's count

TODO: Suneel; Query works in Postman, CLI complains that 40 character 0x address is not 64 characters, does not accept Bech32 address

Here is the top level entry point of the `blockchain` subcommand for `hmy_cli` :

```text

Query Harmony's blockchain for high level metrics, queries

Usage:
  hmy_cli blockchain [flags]
  hmy_cli blockchain [command]

Available Commands:
  block-by-number        Get a harmony blockchain block by block number
  protocol-version       The version of the Harmony Protocol
  transaction-by-hash    Get transaction by hash
  transaction-by-receipt Get transaction by receipt
  transaction-count      Get a transaction's count

Flags:
  -h, --help          help for blockchain
  -l, --latest        Use latest in query
      --node string   <host>:<port> (default "http://localhost:9500")

Global Flags:
  -p, --pretty   pretty print JSON outputs

Use "hmy_cli blockchain [command] --help" for more information about a command.
```

