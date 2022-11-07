# Identities

Cherry Network provides a naming system that allows participants to add personal information to their account.

### Setting an Identity

Users can set their identity by registering through default fields (legal name, display name, email, website, twitter, etc). Users must reserve funds in bond to store their information on chain. These funds are locked, not spent and they are returned when the identity is cleared.

Click on the three dots next to your account and select "Set on-chain identity"

![](<../.gitbook/assets/Screenshot 2022-06-22 at 6.46.45 PM.png>)

A popup window will appear, with the default fields.

![](<../.gitbook/assets/image (13).png>)

### Sub Accounts[​](https://wiki.polkadot.network/docs/learn-identity#sub-accounts) <a href="#sub-accounts" id="sub-accounts"></a>

Users can also link accounts by setting "sub accounts", each with its own identity, under a primary account. The system reserves a bond for each sub account. An example of how you might use this would be a validation company running multiple validators. A single entity, "My Staking Company", could register multiple sub accounts that represent the Stash accounts of each of their validators.

An account can have a maximum of 100 sub-accounts.

Click on the three dots next to your account and select "Set on-chain sub-identities". In the pop-up window, select your sub account you wanna add and enter a name in the sub name field.

![](<../.gitbook/assets/Screenshot 2022-06-22 at 6.57.36 PM.png>)

### Clearing and Killing an Identity

**Clearing:** Users can clear their identity information and have their deposit returned. Clearing an identity also clears all sub accounts and returns their deposits.

To clear an identity:

1. Navigate to the Accounts UI.
2. Click the three dots corresponding to the account you want to clear and select 'Set on-chain identity'.
3. Select 'Clear Identity', and sign and submit the transaction.

![](<../.gitbook/assets/Screenshot 2022-06-22 at 6.52.39 PM.png>)

**Killing:** The Council can kill an identity that it deems erroneous. This results in a slash of the deposit.
