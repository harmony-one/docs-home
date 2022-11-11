# Staking Dashboard

Staking via browser is done via [Staking Dashboard](https://staking.harmony.one/). There you will be able to delegate, undelegate tokens, claim rewards and manage your delegations. Currently, staking transaction are supported on [Ledger Nano S,](../../../../general/wallets/hardware-wallets/ledger/) [ONE Wallet](../../../../general/ecosystem/daos/one-wallet.md) and [Math Wallet](../../../../developers/wallets/mathwallet.md). you can log in or create a new address via those three wallets.

![](<../../../../.gitbook/assets/image (29).png>)

![](<../../../../.gitbook/assets/image (30).png>)

In order to choose their validators and manage their delegation, delegators have access to a range of information on the Staking Dashboard.

![Screen zoomed for demonstration purpose.](<../../../../.gitbook/assets/image (137).png>)

| **Portfolio Page**   | Delegators can claim full rewards and monitor validators in their delegation portfolio.  |
| -------------------- | ---------------------------------------------------------------------------------------- |
| Staked               | Amount of ONE delegated                                                                  |
| Available            | Amount of ONE that available to delegate                                                 |
| Rewards              | Rewards yet to be claimed                                                                |
| Portfolio allocation | Delegation amount across different validators                                            |
| Expected return      | expected annual percentage return rate                                                   |
| Returned in          | Epochs left until undelegation funds will be accessible                                  |
| Reward (up to date)  | Unclaimed rewards                                                                        |
| Status               | Election status of the validator in current epoch                                        |



![Screen shot is zoomed for demonstration purpose.](<../../../../.gitbook/assets/image (132).png>)

| **Validator list**     | Delegators can access necessary information of validators at a glance to choose desired validator(s). |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| Effective Median Stake | Median of ONE staked among the top elected slots                                                      |
| Total Stake            | Total ONE staked in the Harmony network                                                               |
| Current block height   | current block height of Harmony blockchain                                                            |
| All                    | All validators created & listed onchain                                                               |
| Elected                | Validator currently selected & eligible to sign blocks & earn rewards                                 |
| Not Elected            | Validator currently not-selected to sign blocks due to low stake or insufficient uptime               |
| Expected return        | Expected annual return rate                                                                           |
| Stake                  | Total ONE staked by the validator                                                                     |
| Fees                   | Commission on rewards charged by validator                                                            |
| Uptime (AVG)           | Signing percentage for this validator's nodes                                                         |
| Status                 | Election status of validator in current epoch                                                         |
| Name                   | The validators' moniker                                                                               |



![Screen zoomed for demonstration purpose.](<../../../../.gitbook/assets/image (133).png>)

| **Validator Profile**      | Delegators can check detailed information of a validator and delegate/undelegate this validator. |
| -------------------------- | ------------------------------------------------------------------------------------------------ |
| Delegated                  | Total ONE delegated to this validator                                                            |
| Self stake                 | Amount of ONE staked by validator                                                                |
| Max delegation             | Maximum ONE stake allowed by the validator, including self-stake                                 |
| Validator since            | Block number at which validator registered                                                       |
| Fee                        | Commission on rewards charged by validator                                                       |
| Max daily change           | daily change in commission allowed for this validator                                            |
| Uptime (AVG)               | Signing percentage for this validator's nodes                                                    |
| Slots                      | Number of seats (bls keys) associated with the Validator                                         |
| Elected slots              | Number of seats (bls keys) elected in the current committee                                      |
| Expected return            | Expected annual return rate                                                                      |
| Lifetime rewards           | all rewards collected by the validator                                                           |
| Shards                     | Shards in which validator's BLS keys belong, shown order is based on time to add                 |
| Stake & delegation history | Stake and delegation amount for the validator at every epoch                                     |
| Reward rate history        | Expected annual percentage return rate for validator at every epoch                              |
| Delegators                 | List of accounts that delegated to this validator and delegation amount                          |



![](<../../../../.gitbook/assets/image (31) (1).png>)

![](<../../../../.gitbook/assets/image (140).png>)

| **Analytics** | Delegator can access both intuitive and statistical information on the stake distribution among validators and 4 shards. |
| ------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Slots         | The slots occupied by this validator                                                                                     |
| Bid           | Bid per BLS key                                                                                                          |
| Effective     | Validator's effective ONE staked                                                                                         |
| total         | Validator's total ONE staked                                                                                             |
| Self stake    | Amount of ONE staked by validator                                                                                        |
