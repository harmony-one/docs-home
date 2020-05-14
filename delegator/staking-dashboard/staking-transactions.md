# Staking Transactions

## Delegate

Check the validators page to see list of validators. Click on desired validator logo to direct to the Validator profile for more details.

![](../../.gitbook/assets/image%20%2864%29.png)

Click on the "Delegate" button to delegate to this validator.

![](../../.gitbook/assets/image%20%287%29.png)

Enter the desired delegation amount or scroll the percentage slider in the pop-up Delegate window. Delegation must be at least 1000 ONE. Click on "Next" and confirm the signature request.

![](../../.gitbook/assets/image%20%2831%29.png)

![](../../.gitbook/assets/image%20%2822%29.png)

Different wallets use different ways to confirm signature request. Please check the [Wallet](https://app.gitbook.com/@harmony-one/s/home/~/drafts/-M7F2-rR3OLvk7_5kftG/wallets) section for details.

Once transaction is signed, Delegate window will pop-up on the staking dashboard and display the transaction status.

![](../../.gitbook/assets/image%20%28175%29.png)

![](../../.gitbook/assets/image%20%2812%29.png)

## Undelegate

If a delegator decides to stop delegating to a validator, he or she can choose to undelegate their tokens from the validator. After undelegation is initiated from a currently elected validator, the tokens will be locked for 7 [epochs](https://docs.harmony.one/home/validators/definitions/epoch-transition) \(10.5 days\) before being credited to the delegator’s account balance. Note that the unlocking of the undelegated tokens only happens at the end of every epoch. Locked tokens are still slashable if the validator double signs.

For undelegating from a non-elected validator, the token will be unlocked 7 epochs after the validator was last elected. For example, if you are undelegating from a validator who was last elected 3 epochs ago, your token will be locked for 4 epochs after the undelegation starts. This leads to a convenient result that if you undelegate from a validator who is never elected before, you can have your token returned in the current epoch.

## 

