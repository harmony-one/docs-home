---
description: >-
  An overview of questions, additional resources, and products relating to
  Harmony’s Open Staking.
---

# FAQ

## **1.** **How to Stake Harmony \($ONE\)?**

You can participate in Harmony’s Staking either as a **delegator** or a **validator.**

_**For Delegators:**_ For those wishing to participate in staking without running a validator, delegation is the best approach to still get involved and earn block rewards. Harmony ONE holders can delegate their tokens to existing validators using our staking explorer:[ https://staking.harmony.one/](https://staking.harmony.one/). If the tokens are delegated to an elected validator, a portion of the block reward earned by the validator will be credited to the delegator \(according to section Block Reward\).The earned block rewards are stored in a separate reward balance of the delegator, which can be immediately withdrawn to the delegator’s account balance. The block rewards can also be staked again to achieve the compounding effect of staking. Your delegated tokens are also associated with slashing risks of the validator. As a delegator, you should carefully choose validators based on their historical performance metrics such as APR, uptime and commission. In case of indifference or indecisiveness, you should distribute your delegations among multiple validators in order to minimize risk.

_**For Validators:**_ Validators are invited to follow this [Step by Step guide](../../validators/), to start earning staking rewards!

## **2. How to Stake Harmony \($ONE\)? How much can I expect to earn?**

While rewards are not fixed, and depend on the performance of a validator, the total staked tokens on the network, and the efficiency of the validator to follow Harmony’s Effective Proof of Stake.

You can check the median Expected Return \(from the last 30 epochs\) on [Harmony’s Staking dashboard](http://staking.harmony.one/). When you click on a validator on the staking dashboard you can also see the latest Expected return \(from the last epoch\). The percentage shown is the APY \(annual percentage yield\).

## **3. What do the Total Stake values on the Staking Dashboard mean?**

When you land on [Harmony’s Staking dashboard](http://staking.harmony.one/), you see the list of Validators.  
There is a ‘_Total Stake_’ value on the top center. This value represents the total stake contributed to the network by ALL the validators, irrespective of whether they are currently elected in the top 800 available slots and signing blocks. This value includes stake from ALL validators created on the network.

In the _Analytics section_ \([staking.harmony.one/analytics](https://staking.harmony.one/analytics)\), you see two tabs. The tab for ‘_Last Epoch_’ shows the results of the last election for the top 800 slots in the network. The total stake and effective median value in this section determine the validator list and block rewards for the current epoch. The tab for ‘_Next Epoch_’ shows the real-time snapshot values of total stake and effective median, which means that these values will be used for election right before the next epoch starts. You may notice that the total stake value in the _‘Last Election_’ and ‘_Next election_’ may be different. This is because if a validator who got elected in the last election is not signing enough blocks, then they may not qualify for the upcoming election before the next epoch. As a result, their stake gets discounted in the ‘_Next Election_’ stake calculation.

## **4. Why is the ‘**_**Expected Return’**_ **value 0 for validators?**

The _Expected return value_ will start to show real non-zero values after a validator completes one full epoch after getting elected. This is because when a validator gets elected for the first time, there is no historical data to estimate expected returns.

## **5. What does** _**Lifetime reward**_ **mean?**

_Lifetime reward_ means the total cumulative ONE earned by that validator.

## **6. I delegated and my validator is earning, but I can’t see my reward. Why?**

Check for your rewards earned in the Portfolio page of the staking dashboard.

## **7. I sent 1 ONE to the dashboard but it’s not showing**

When you send 1 ONE, what you will get is 0.99 ONE due to transaction fee. However, the staking dashboard doesn’t support decimal places currently.

## **8. Is reward per validator/delegator fixed?**

No, it consists of the validator’s effective stake, uptime and total stake within a shard.

## **9. I want to undelegate my token, how long do I have to wait?**

Tokens take 1 epoch to be undelegated \(so you can redelegate them to another validator\). You need to wait though 7 epochs if you want the tokens back to your wallet.

## **10. My validator wasn’t elected, can I undelegate and stake to another validator?**

Yes, you can.

## **11. How can I change my wallet password?**

Ensure you have access to your seed phrase or private key first. For [One Wallet](../../wallets/browser-extensions-wallets/one-wallet.md), uninstall the extension and install it again. Launch the extension and choose the option to recover your account. Enter your seed or private key and input your new password.

## **12. Is there a window between epochs to delegate tokens?**

There is no window between epochs, however, you can collect rewards close to the end of the current epoch, and immediately delegate, to be active and earning rewards in the next epoch.

## **13. What does Fee mean?**

It is the amount that the validator will charge from the generated rewards for services rendered \(running servers, maintenance, maintaining high uptime\).

## **14. Unable to claim rewards, what can I do?**

Please ensure you have enough to cover gas fee. Gas fee is deducted from your Available balance and not from the reward you’ve earned.

## **15. What’s the minimum claim amount for delegators?**

1 ONE

## **16. What is the minimum stake amount for delegators?**

100 ONEs.

## **17. How long does an epoch last?**

It depends on the blocktime.  
Currently 1 epoch has 32768 blocks and with a 2s blocktime this is around **18.2 hours.**

## **18. Are there any risks involved with Harmony Staking?**

There are risks associated with Staking on Harmony.

Among those could be the following:

* Account lost: Mnemonic/Private key backup
* Firmware Problems
* Network Centralization
* Price Volatility of $ONE Coins
* Technical Debt

