# Become a Nominator

Nominators are one type of participant in the staking process of Cherry Chain. They are responsible for appointing their stake to the validators, who are the second type of participant. By appointing their stake, they are able to elect the active set of validators and share in the rewards that are paid out.

While the validators are active participants in the network that engage in the block production and finality mechanisms, nominators take a slightly more passive role. Being a nominator does not require running a node of your own or worrying about online uptime. However, a good nominator performs due diligence on the validators that they elect. When looking for validators to nominate, a nominator should pay attention to their own reward percentage for nominating a specific validator - as well as the risk that they bear of being slashed if the validator gets slashed.

## Setting up Stash and Controller keys

Nominators are recommended to set up separate stash and controller accounts. Explanation and reasoning for generating distinct accounts for this purpose is elaborated here.

You can generate your stash and controller account via any of the recommended methods that are detailed on the [account generation](https://docs.cherry.network/quickstart/create-an-account) page.

### Step 1: Bond your tokens

On the UI navigate to the “**Staking”** tab (within the “**Network”** menu). The “**Staking** **Overview”** subsection will show you all the active validators and their information/identities, the amount of CHER that are staking for them, the amount that is their own provided stake, how much they charge in commission, the era points they've earned in the current era, and the last block number that they produced. If you click on the chart button it will take you to the “**Validator** **Stats**" page for that validator that shows you more detailed and historical information about the validator's stake, rewards and slashes.

The “**Account** **actions**” subsection allows you to stake and nominate. Click it, and then click the “**+ Nominator**” button.

You will see a window like the one below:

![](<../../.gitbook/assets/image (15).png>)

Select a “**value bonded**” that is less than the total amount of tokens you have, so you have some left over to pay transaction fees. Also be mindful of the reaping threshold - the amount that must remain in an account lest it be burned. That amount is 1 CHER, so it's recommended to keep at least 1.5 CHER in your account to be on the safe side. Choose whatever payment destination that makes sense to you. If you're unsure, you can choose "**Stash** **account**” (increase amount at stake) to simply accrue the rewards into the amount you're staking and earn compound interest.

### Step 2: Nominate a validator

You are now bonded. Being bonded means that your tokens are locked and could be slashed if the validators you nominate misbehave. All bonded funds can now be distributed to validators. Be careful about the validators you choose since you will be slashed if your validator commits an offence.

![](<../../.gitbook/assets/image (16).png>)

Select them, confirm the transaction, and you're done - you are now nominating. Your nominations will become active in the next era. Eras last 1 hour in Cherry Network. Depending on when you do this, your nominations may become active almost immediately, or you may have to wait almost the entire 1 hour before your nominations are active. You can check how far along Cherry is in the current era on the ”**Staking Page**”.

Assuming at least one of your nominations ends up in the active validator set, you will start to get rewards allocated to you. In order to claim them (i.e., add them to your account), you must manually claim them.

### Step 3: Stop nominating

At some point, you might decide to stop nominating one or more validators. You can always change who you're nominating, but you cannot withdraw your tokens unless you unbond them. Detailed instructions are available [here](https://docs.cherry.network/cherry-node/consensus/unbonding-and-rebonding).
