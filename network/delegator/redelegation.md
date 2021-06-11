# Redelegation

To minimize the friction of delegation and allow delegators to easily switch between validators, redelegation feature is supported in Harmony Staking. If a delegator wants to redelegate tokens from one validator to another, he or she can undelegate the tokens which will be locked immediately. After that, any new delegations will try to utilize the locked tokens first and, if not enough, the liquid tokens from the user's wallet. Note the locked tokens are only available for redelegation after the end of the epoch when they were first undelegated. This is to make sure the tokens can still be slashed within the same epoch of undelegation if they are used for malicious double signing.

![Undelegated tokens are available for delegation after the epoch of undelegation](https://miro.medium.com/max/1485/1*0YYTOLOAdHDaccQTrPZGIA.jpeg)

Specifically, if stakers want to redelegate X tokens from validator A to validator B, they can first undelegate the X tokens from validator A and the tokens will be locked immediately. After the end of the epoch, they can send a delegate transaction with X tokens to validator B and the locked tokens will be immediately unlocked and used for the new delegation. Alternatively, If the delegation amount is greater than the locked tokens that’s available for redelegation, the liquid tokens will be used to fill the difference.

With the restoration of 7 epoch locking period and the newly introduced redelegation support, we are bringing back the security guarantee of the original EPoS model without significantly affecting the existing stakers’ workflow. For more discussion and proposal about Harmony network, feel free to write a post at [https://talk.harmony.one/](https://talk.harmony.one/).

