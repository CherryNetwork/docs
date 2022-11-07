---
description: An FAQ page for Staking and Nominating questions.
---

# Validating FAQ

## General <a href="#what-is-the-maximum-annual-interest-and-rewards-possible-when-nominating-or-validating" id="what-is-the-maximum-annual-interest-and-rewards-possible-when-nominating-or-validating"></a>

#### What is the maximum annual interest and rewards possible when nominating or validating? <a href="#what-is-the-maximum-annual-interest-and-rewards-possible-when-nominating-or-validating" id="what-is-the-maximum-annual-interest-and-rewards-possible-when-nominating-or-validating"></a>

Returns will vary based on several factors including, how many CHER are staked for a given validator, how much your proportion is in that stake, and how many validators are in the set at a given time. Annual inflation of the CHER supply will not exceed 30%. Rewards from validating is expected to be \~20% annually, assuming no slashing and remaining in the validator set the entire time. Note that only some of the rewards come from supply inflation; other rewards come from transaction fees, tips, and the like. Maximum rewards are obtained when the percentage of all CHERs staked is at 75%.

#### Why can't I see any staking or validation rewards? <a href="#why-cant-i-see-any-staking-rewards" id="why-cant-i-see-any-staking-rewards"></a>

Unless and until you choose the options of rewards to be paid in the stash account or controller account instead of the default option of bonding earned rewards, you won't see any transactions (on subscan) of rewards to your account. If you had chosen the default option, you will see an increase in the bonded amount after claiming the payout(s) by you or anyone from the nominators or the validator.

#### How can one claim the staking or validation rewards? <a href="#how-can-one-claim-the-staking-rewards" id="how-can-one-claim-the-staking-rewards"></a>

The staking rewards corresponding to a validator need to be claimed by a single transaction within 84 eras. Anyone from the validator or corresponding nominators can claim the rewards for everyone (top 256 nominators) by paying the transaction fees. If no one does it, rewards expire after 84 eras \[84\*(era length of 6 hours) = 504 hours i.e. 21 days]. Frequent rewards claiming could give better the compounding effect. However, beware that claiming payouts on behalf of all nominators and the validator could result in significant transaction fees.

## Staking <a href="#what-is-staking" id="what-is-staking"></a>

Find an answer to all your staking related questions.

#### What is staking? <a href="#what-is-staking" id="what-is-staking"></a>

Staking allows CHER holders to participate in the security and availability of Cherry by leveraging their tokens to validate. Validators who stake CHER, have an operational validator node, and behave honestly will get rewarded with CHER. Actors who misbehave or who are unavailable/offline will have a portion of their stake slashed as a penalty.

#### What are the annual returns for staking? <a href="#what-are-the-annual-returns-for-staking" id="what-are-the-annual-returns-for-staking"></a>

The exact number will vary depending on the amount of CHER staked. We'll update this as we know more.

#### What do I need to stake? <a href="#what-do-i-need-to-stake" id="what-do-i-need-to-stake"></a>

To become a validator, you need a computer with recently up-to-date specifications, a stable and fast internet connection, and CHER to stake. If you do not have CHER to stake, it is also possible to convince nominators to nominate you. Once you have acquired enough stake to make it into the validator set, you will start validating.To become a nominator, you only need to have some CHER to stake.

#### What is nominating? <a href="#what-is-nominating" id="what-is-nominating"></a>

A nominator publishes a list of validator candidates that they trust, and puts down an amount of CHER at stake to support them with. If some of these candidates are elected as validators, they share with them the payments, or the sanctions, on a per-staked-CHER basis. Unlike validators, an unlimited number of parties can participate as nominators. As long as a nominator is diligent in their choice and only supports validator candidates with good security practices, their role carries low risk and provides a continuous source of revenue.

#### Can I nominate multiple validators? <a href="#can-i-nominate-multiple-validators" id="can-i-nominate-multiple-validators"></a>

Yes. Validators are selected via the Phragmen Method. You can think of this is a version of "approval voting" - you can approve zero, one, or multiple validators (although of course, if you do not nominate any validators, you are not nominating and thus will not receive any rewards).For a more in-depth explanation of Phragmen, please see the [Polkadot Wiki Phragmen](https://wiki.polkadot.network/en/latest/polkadot/learn/phragmen/) page.

#### What do I need to nominate? <a href="#what-do-i-need-to-nominate" id="what-do-i-need-to-nominate"></a>

All you need are some CHER and decide which validator to nominate.

#### What factors affect staking rewards? <a href="#what-factors-affect-staking-rewards" id="what-factors-affect-staking-rewards"></a>

Consider the following factors/parameters while staking:

* Lesser the commission, the higher your rewards will be.
* Nominating multiple validators will reduce the risk in case any slashing event occurs. {So far no validator performed any malicious activity}
* Validators with a low total stake (self+nominated stake) will yield more reward per CHER. But be sure your chosen validator has enough stake to maintain its position in the top 95 rankings by the total stake.

If you nominate to validator(s) having 100% commission (private validators) will get all your rewards and you won't receive any rewards.

## Validating <a href="#why-should-i-validate-on-edgeware" id="why-should-i-validate-on-edgeware"></a>

#### Why should I validate on Cherry Network? <a href="#why-should-i-validate-on-edgeware" id="why-should-i-validate-on-edgeware"></a>

Cherry is a proof-of-stake network, which requires Validators to ensure transactions are well-formed and to provide security on Cherry. Validators also earn fees from both the block reward and transactions. Earned tokens can then be used to influence further governance decisions on the network.

#### I have ‘x’ active nomination(s), ‘y’ inactive nomination(s) and ‘z’ awaiting nomination(s) corresponding to my stash. What does it mean? <a href="#i-have-x-active-nomination-s-y-inactive-nomination-s-and-z-awaiting-nomination-s-corresponding-to-my" id="i-have-x-active-nomination-s-y-inactive-nomination-s-and-z-awaiting-nomination-s-corresponding-to-my"></a>

Active nominations indicate the nominations corresponding to which you are receiving the staking rewards. Ideally, all your nominations should be active, if not it means you are getting staking rewards partially for your stash.Inactive nominations indicate your nominated validators which are currently offline. You need to stop nominations and renominate again to active validators to receive staking rewards corresponding to your whole stash. (Here, to stop nominations and renominate you don't need to unbond funds from your stash.)Awaiting nominations are the ones which you recently nominated and they will be added to active nominations after a cycle of the era(6 hours).

