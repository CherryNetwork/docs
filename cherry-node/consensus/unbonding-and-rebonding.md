# Unbonding and Rebonding

The following guide describes how to stop nominating or validating and retrieve your stake. Please note that all networks on which you can nominate have a delayed exit period, called the **unbonding period**, which serves as a cooldown. You will not be able to transfer your tokens before this period has elapsed, and you will not receive any staking rewards during this period (as you are not nominating any validators). In Cherry Network, the **unbonding period** is **28 days.**

#### Step 1: Stop Nominating

Navigate to the "Staking" tab. On this tab click on the "**Account Actions**" tab at the top of the screen. Here, click "**Stop**" on an account you're staking with and would like to free the funds for. This will "chill" the tokens. After you confirm this transaction, your tokens will still remain **bonded**. This means they stay ready to be distributed among nominees or used as validator self-stake again. To actually withdraw them, you need to unbond.

![](<../../.gitbook/assets/image (20).png>)

#### Step 2: Unbonding an amount

To unbond the amount, click the three dots next to the account you want to unbond tokens for, and select "Unbond funds".

Select the amount you wish to unbond and click Unbond, then confirm the transaction. If successful, your balance will show as "unbonding" with an indicator of how many more blocks remain until the amount is fully unlocked. This duration varies depending on the network you're on. The bonding duration on Cherry Network is **28 days**.

![](<../../.gitbook/assets/image (5).png>)

Once this process is complete, you will have to issue another, final transaction: Withdraw Unbonded, which will be available in the same pop-up.

![](<../../.gitbook/assets/image (6).png>)

You can also check how long you have to wait in order to withdraw your stake in the Accounts page by expanding your account balance. There is a tiny icon beside your tokens waiting to be unbonded, that will eventually become an unlock icon once the remaining blocks get passed.

![](<../../.gitbook/assets/image (7) (1).png>)

Then, you can click that icon directly to submit the withdraw transaction. Finally, your transferrable balance will increase by the amount of tokens you've just fully unbonded.

### Rebonding before the end of the unbonding period

If you want to rebond your tokens before the unbonding period is over, you can do this by issuing a `rebond`. This allows you to bond your tokens that are still locked without waiting until the end of the unbonding period.

To rebond, click the three dots next to the account you want to rebond tokens for, and select “Rebond funds”. Enter the amount of tokens that are currently locked in unbonding that you want to rebond in "rebonded amount”. Then click "Rebond".

![](<../../.gitbook/assets/image (4) (1).png>)

![](<../../.gitbook/assets/image (10) (1).png>)

Confirm the transaction in the next pop-up. Once the transaction is included in the next block your tokens will be rebonded again and you can start staking with them.
