# Staking Transactions

## Delegate

If the tokens are delegated to an elected validator, a portion of the block reward earned by the validator will be credited to the delegator

#### Delegate transaction

Check the validators page to see list of validators. Click on desired validator logo to direct to the Validator profile for more details.

![](../../.gitbook/assets/image%20%2866%29.png)

Click on the "Delegate" button to delegate to this validator.

![](../../.gitbook/assets/image%20%289%29.png)

Enter the desired delegation amount or scroll the percentage slider in the pop-up Delegate window. Delegation must be at least 1000 ONE. Click on "Next" and confirm the signature request.

![](../../.gitbook/assets/image%20%2833%29.png)

![](../../.gitbook/assets/image%20%2824%29.png)

Different wallets use different ways to confirm signature request. Please check the [Wallet](https://app.gitbook.com/@harmony-one/s/home/~/drafts/-M7F2-rR3OLvk7_5kftG/wallets) section for details.

Once transaction is signed, Delegate window will pop-up on the staking dashboard and display the transaction status.

![](../../.gitbook/assets/image%20%28181%29.png)

![](../../.gitbook/assets/image%20%2814%29.png)

## Undelegate

If a delegator decides to stop delegating to a validator, he or she can choose to undelegate their tokens from the validator. After undelegation is initiated from a currently elected validator, the tokens will be locked for 7 [epochs](https://docs.harmony.one/home/validators/definitions/epoch-transition) \(10.5 days\) before being credited to the delegator’s account balance. Note that the unlocking of the undelegated tokens only happens at the end of every epoch. Locked tokens are still slashable if the validator double signs.

For undelegating from a non-elected validator, the token will be unlocked 7 epochs after the validator was last elected. For example, if you are undelegating from a validator who was last elected 3 epochs ago, your token will be locked for 4 epochs after the undelegation starts. This leads to a convenient result that if you undelegate from a validator who is never elected before, you can have your token returned in the current epoch.

#### Undelegate transaction

Click the "Undelegate" button on validator profile.

![](../../.gitbook/assets/image%20%28150%29.png)

Signing process same as Delegate transactions.

This transaction will display on the Pending Undelegations section on the Portfolio page.

![](../../.gitbook/assets/image%20%28115%29.png)

## Claim rewards

The earned block rewards are stored in a separate reward balance of the delegator, which can be immediately withdrawn to the delegator’s account balance. The block rewards can also be staked again to achieve the compounding effect of staking. You can only claim full rewards, not partially.

#### Claim Rewards transaction

Click on Claim Rewards button.

![](../../.gitbook/assets/image%20%2894%29.png)

![](../../.gitbook/assets/image%20%288%29.png)

Signing process same as Delegate transactions.

