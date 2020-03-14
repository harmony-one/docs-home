# Cookbook

The easiest way to get detailed help is to use the cli itself. For example below is the cookbook which gives an overview of various commands.

```text
[ec2-user@ip-172-31-45-84 ~]$ ./hmy cookbook

Cookbook of Usage

Note:

1) Every subcommand recognizes a '--help' flag
2) If a passphrase is used by a subcommand, one can enter their own passphrase interactively
   with the --passphrase option. Alternatively, one can pass their own passphrase via a file
   using the --passphrase-file option. If no passphrase option is selected, the default
   passphrase of '' is used.
3) These examples use shard 1 of Mainnet as argument for --node

Examples:

1.  Check account balance on given chain
hmy --node="https://api.s1.t.hmny.io/" balances <SOME_ONE_ADDRESS>

2.  Check sent transaction
hmy --node="https://api.s1.t.hmny.io" blockchain transaction-by-hash <SOME_TX_HASH>

3.  List local account keys
hmy keys list

4.  Sending a transaction (waits 40 seconds for transaction confirmation)
hmy --node="https://api.s1.t.hmny.io/" transfer \
    --from one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw \
    --to one1q6gkzcap0uruuu8r6sldxuu47pd4ww9w9t7tg6 \
    --from-shard 0 --to-shard 1 --amount 200

5.  Sending a batch of transactions as dictated from a file (the `--dry-run` options still apply)
hmy --node="https://api.s1.t.hmny.io/" transfer --file <PATH_TO_JSON_FILE>

    Example of JSON file format:
      [
        {
          "from": "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7",
          "to": "one1zksj3evekayy90xt4psrz8h6j2v3hla4qwz4ur",
          "from-shard" : "0",
          "to-shard": "0",
          "amount": "1",
          "passphrase-string": "",
          "nonce": "1",
          "stop-on-error": true
        },
        {
          "from": "one103q7qe5t2505lypvltkqtddaef5tzfxwsse4z7",
          "to": "one1zksj3evekayy90xt4psrz8h6j2v3hla4qwz4ur",
          "from-shard" : "0",
          "to-shard": "0",
          "amount": "1",
          "passphrase-file": "./pw.txt"
        }
      ]

6.  Check a completed transaction receipt
hmy --node="https://api.s1.t.hmny.io" blockchain transaction-receipt <SOME_TX_HASH>

7.  Import an account using the mnemonic. Prompts the user to give the mnemonic.
hmy keys recover-from-mnemonic <ACCOUNT_NAME>

8.  Import an existing keystore file
hmy keys import-ks <PATH_TO_KEYSTORE_JSON>.key

9.  Import a keystore file using a secp256k1 private key
hmy keys import-private-key <secp256k1_PRIVATE_KEY>

10.  Export a keystore file's secp256k1 private key
hmy keys export-private-key <ACCOUNT_ADDRESS> --passphrase

11. Generate a BLS key then encrypt and save the private key to the specified location.
hmy keys generate-bls-key --bls-file-path /tmp/file.key

12. Create a new validator with a list of BLS keys
hmy --node="https://api.s0.t.hmny.io" staking create-validator --amount 10 --validator-addr <SOME_ONE_ADDRESS> \
    --bls-pubkeys <BLS_KEY_1>,<BLS_KEY_2>,<BLS_KEY_3> \
    --identity foo --details bar --name baz --max-change-rate 0.1 --max-rate 0.1 --max-total-delegation 10 \
    --min-self-delegation 10 --rate 0.1 --security-contact Leo  --website harmony.one --passphrase

13. Edit an existing validator
hmy --node="https://api.s0.t.hmny.io" staking edit-validator \
    --validator-addr <SOME_ONE_ADDRESS> --identity foo --details bar \
    --name baz --security-contact EK --website harmony.one \
    --min-self-delegation 0 --max-total-delegation 10 --rate 0.1\
    --add-bls-key <SOME_BLS_KEY> --remove-bls-key <OTHER_BLS_KEY> --passphrase

14. Delegate an amount to a validator
hmy --node="https://api.s0.t.hmny.io" staking delegate \
    --delegator-addr <SOME_ONE_ADDRESS> --validator-addr <VALIDATOR_ONE_ADDRESS> \
    --amount 10 --passphrase

15. Undelegate to a validator
hmy --node="https://api.s0.t.hmny.io" staking undelegate \
    --delegator-addr <SOME_ONE_ADDRESS> --validator-addr <VALIDATOR_ONE_ADDRESS> \
    --amount 10 --passphrase

16. Collect block rewards as a delegator
hmy --node="https://api.s0.t.hmny.io" staking collect-rewards \
    --delegator-addr <SOME_ONE_ADDRESS> --passphrase

17. Check elected validators
hmy --node="https://api.s0.t.hmny.io" blockchain validator elected

18. Get current staking utility metrics
hmy --node="https://api.s0.t.hmny.io" blockchain utility-metrics

19. Check in-memory record of failed staking transactions
hmy failures staking

20. Check which shard your BLS public key would be assigned to as a validator
hmy utility shard-for-bls 2d61379e44a772e5757e27ee2b3874254f56073e6bd226eb8b160371cc3c18b8c4977bd3dcb71fd57dc62bf0e143fd08

[ec2-user@ip-172-31-45-84 ~]$ ./hmy
```

