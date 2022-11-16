# Treasury

The Treasury is a pot of funds collected through a portion of block production rewards, transaction fees, slashing and staking inefficiencies.

The funds held in the Treasury can be spent by making a spending proposal that, if approved by the Council, will enter a waiting period before distribution. This waiting period is known as the spend period with the current default set to 28 days. The Treasury attempts to spend as many proposals in the queue as it can without running out of funds.

Treasury payout is an automatic process:

* If the Treasury funds run out with approved proposals left to fund, the votes on those proposals reset, and the Council needs to vote those proposals again. If the proposal is recurring, it loses the funding for that segment.
* If the Treasury ends a spend period without spending all of its funds, it suffers a burn of a percentage of its funds - thereby causing deflationary pressure. This encourages the spending of the funds in the Treasury by the Council. This percentage is currently at 1% on Cherry Chain.

When a stakeholder wishes to propose a spend from the Treasury, they must reserve a deposit of at least 5% of the proposed spend (or 1000 CHER, whichever is highest). This deposit will be slashed if the proposal is rejected, and returned if it is accepted.

The Council governs the Treasury and how the funds are spent is up to their judgment.

{% hint style="warning" %}
The Council does not approve or deny Treasury Proposals based on the funds available in the Treasury. In other words, proposals are not approved just because there are funds ready to spend but are subject to a burn.
{% endhint %}

### Funding The Treasury

The Treasury is funded from different sources:

1. **Slashing**: When a validator is slashed for any reason, the slashed amount is sent to the Treasury with a reward going to the entity that reported the validator (another validator). The reward is taken from the slash amount and varies per offence and number of reporters.
2. **Transaction fees**: A portion of each block’s transaction fees goes to the Treasury, with the remainder going to the block author.
3. **Staking inefficiency**: Inflation is designed to be 10% in the first year, and the ideal staking ratio is set at 50%, meaning half of all tokens should be locked in staking. Any deviation from this ratio will cause a proportional amount of the inflation to go to the Treasury. In other words, if 50% of all tokens are staked, then 100% of the inflation goes to the validators as reward. If the staking rate is greater than or less than 50%, then the validators will receive less, with the remainder going to the Treasury.

### Creating a Treasury Proposal

The proposer has to deposit 5% of the requested amount or 1000 CHER (whichever is higher) as an anti-spam measure. This amount is burned if the proposal is rejected, or refunded otherwise. These values may change in the future.

Please note that there is no way for a user to revoke a treasury proposal after it has been submitted. The Council will either accept or reject the proposal, and if the proposal is rejected, the bonded funds are burned.

#### Announcing the Proposal

To minimize storage on chain, proposals don't contain contextual information. When a user submits a proposal, they will probably need to find an off-chain way to explain the proposal.&#x20;

Community members who want to participate in the discussion about proposals should join the [Cherry Network DAO](https://dao.cherry.network/c/governance/). In there you can:

* Fill in a form about your proposal. Other community members can join a discussion about your proposal.
* Find proposal forms and discuss with other community members.

#### Creating the Proposal

To create a proposal use the "Submit proposal" button in the `Governance -> Treasury` tab. A popup window will appear (see image below) with the following fields:

![Treasury proposal example](../../../../Desktop/Screenshot%202022-11-16%20at%2012.34.43%20PM.png "treasury proposal example")

1. In the **value** field, you enter the desired amount of CHER.
2. In the **beneficiary** field, you enter the recipient of the above amount.
3. In the **segments** field, you enter the number of spend periods that the recipient will be getting a portion of the above amount. **Example:** Let’s say that you want 10.000 CHER over 4 spend periods (occurs). That means that the recipient will be getting 2.500 CHER each spend period, for 4 spend periods, for a total of 10.000 CHER (10.000 / 4 = 2.500).
4. Also, a button will appear "Select this or the next cycle", giving you the option to create a proposal on the next spend period.

The system will automatically take the required deposit, picking the higher of the two values mentioned above.

Once created, your proposal will become visible in the Treasury screen and the Council can start voting on it.

In the Treasury screen you will also see a field called "Segments". There you can see the current segment of a recurring proposal, and the remaining segments.

Remember that the proposal has no metadata, so it's up to the proposer to create a description and purpose that the Council could study and base their votes on.

At this point, a Council member can create a motion to accept or to reject the treasury proposal. It is possible that one motion to accept and another motion to reject are both created. The proportions to accept and reject Council proposals vary between accept or reject. The threshold for accepting a treasury proposal is at least three-fifths of the Council. On the other hand, the threshold for rejecting a proposal is at least one-half of the Council.

The threshold for accepting a treasury proposal is at least three-fifths of the Council. On the other hand, the threshold for rejecting a proposal is at least one-half of the Council.
