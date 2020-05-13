# Undelegation

If a delegator decides to stop delegating to a validator \(including self-undelegation\), he or she can choose to undelegate their tokens from the validator. After undelegation is initiated from a currently elected validator, the tokens will be locked for 7 epochs before being credited to the delegator’s account balance. Note that the unlocking of the undelegated tokens only happens at the end of every epoch. Locked tokens are still slashable if the validator double signs.

For undelegating from a non-elected validator, the token will be unlocked 7 epochs after the validator was last elected. For example, if you are undelegating from a validator who was last elected 3 epochs ago, your token will be locked for 4 epochs after the undelegation starts. This leads to a convenient result that if you undelegate from a validator who is never elected before, you can have your token returned in the current epoch.

