# Cherry Protocol

This page serves as a high-level introduction to the Cherry protocol with terminology that may be specific to Cherry, notable differences to other chains that you may have worked with, and practical information for dealing with the chain.

### Tokens[​](https://wiki.polkadot.network/docs/build-protocol-info#tokens) <a href="#tokens" id="tokens"></a>

* **Token decimals:**
  * Cherry (CHER): 18
  * **Balance type:** [`u128`](https://doc.rust-lang.org/std/u128/index.html)

### Addresses[​](https://wiki.polkadot.network/docs/build-protocol-info#addresses) <a href="#addresses" id="addresses"></a>

In Cherry (and most Substrate chains), user accounts are identified by a 32-byte (256-bit) `AccountId`. This is often, but not always, the public key of a cryptographic key pair.

Cherry (and Substrate) use the SS58 address format. This is a broad "meta-format" designed to handle many different cryptographic schemes and chains. It has much in common with Bitcoin's Base58Check format such as a version prefix, a hash-based checksum suffix, and base-58 encoding.

See the [SS58 page](https://docs.substrate.io/v3/advanced/ss58/) in the Substrate documentation for encoding information and a more comprehensive list of network prefixes.

> **Warning:** Do not use regular expressions (regex) to validate addresses. Always verify using the prefix and checksum of the address. Substrate API Sidecar provides an `accounts/{accountId}/validate` path that returns a boolean `isValid` response for a provided address. If you want to validate addresses in another way, see the [validation documentation](https://docs.substrate.io/v3/advanced/ss58/#validating-addresses).

Relevant SS58 prefixes for this guide:

* Polkadot: 0
* Kusama: 2
* Westend: 42

#### Cryptography[​](https://wiki.polkadot.network/docs/build-protocol-info#cryptography) <a href="#cryptography" id="cryptography"></a>

Cherry supports the following [cryptographic](https://wiki.polkadot.network/docs/learn-cryptography) key pairs and signing algorithms:

* Ed25519
* Sr25519 - Schnorr signatures on the Ristretto group
* ECDSA signatures on secp256k1

Note that the address for a secp256k1 key is the SS58 encoding of the _hash of the public key_ in order to reduce the public key from 33 bytes to 32 bytes.

### Existential Deposit[​](https://wiki.polkadot.network/docs/build-protocol-info#existential-deposit) <a href="#existential-deposit" id="existential-deposit"></a>

Cherry, and most Substrate-based chains, use an _existential deposit_ (ED) to prevent dust accounts from bloating chain state. If an account drops below the ED, it will be _reaped,_ i.e. completely removed from storage and the nonce reset. Cherry's ED is 1 CHER. You can always verify the existential deposit by checking the [chain state](https://polkadot.js.org/apps/#/chainstate) for the constant `balances.existentialDeposit`.

Likewise, if you send a transfer with value below the ED to a new account, it will fail. Custodial wallets should set a minimum withdrawal amount that is greater than the ED to guarantee successful withdrawals.

Wallets and custodians who track account nonces for auditing purposes should take care not to have accounts reaped, as users could refund the address and try making transactions from it. The Balances pallet provides a `transfer_keep_alive` function that will return an error and abort rather than make the transfer if doing so would result in reaping the sender's account.

> **Please be advised**: The existential deposit is a property of the Relay Chain. Your account on the Relay Chain has no direct impact on parachains as you have seperate accounts on each parachain. Still, parachains are able to define an existential deposit of their own, but this is seperate to that of the Relay Chain ED.

### Free vs. Reserved vs. Locked vs. Vesting Balance[​](https://wiki.polkadot.network/docs/build-protocol-info#free-vs-reserved-vs-locked-vs-vesting-balance) <a href="#free-vs-reserved-vs-locked-vs-vesting-balance" id="free-vs-reserved-vs-locked-vs-vesting-balance"></a>

Account balance information is stored in [`AccountData`](https://docs.substrate.io/rustdocs/latest/pallet\_balances/struct.AccountData.html). Cherry primarily deals with two types of balances: free and reserved.

For most operations, free balance is what you are interested in. It is the "power" of an account in staking and governance, for example. Reserved balance represents funds that have been set aside by some operation and still belong to the account holder, but cannot be used.

Locks are an abstraction over free balance that prevent spending for certain purposes. Several locks can operate on the same account, but they overlap rather than add. Locks are automatically added onto accounts when tasks are done on the network (e.g. leasing a parachain slot or voting), these are not customizable. For example, an account could have a free balance of 200 CHER with two locks on it: 150 CHER for `Transfer` purposes and 100 CHER for `Reserve` purposes. The account could not make a transfer that brings its free balance below 150 CHER, but an operation could result in reserving CHER such that the free balance is below 150, but above 100 CHER.

Bonding tokens for staking and voting in governance referenda both utilize locks.

Vesting is another abstraction that uses locks on free balance. Vesting sets a lock that decreases over time until all the funds are transferable.

More info:

* [Lockable Currency](https://docs.substrate.io/rustdocs/latest/frame\_support/traits/trait.LockableCurrency.html)
* [Lock Withdraw Reasons](https://docs.substrate.io/rustdocs/latest/frame\_support/traits/enum.WithdrawReason.html)
* [Vesting](https://docs.substrate.io/rustdocs/latest/pallet\_vesting/struct.Vesting.html)

### Extrinsics and Events[​](https://wiki.polkadot.network/docs/build-protocol-info#extrinsics-and-events) <a href="#extrinsics-and-events" id="extrinsics-and-events"></a>

#### Extrinsics[​](https://wiki.polkadot.network/docs/build-protocol-info#extrinsics) <a href="#extrinsics" id="extrinsics"></a>

Extrinsics constitute information from the outside world and take on three forms:

* Inherents
* Signed Transactions
* Unsigned Transactions

While using Cherry as a user or developer, you will deal almost exclusively with signed transactions. You will, however, see other extrinsics within the blocks that you may decode. Find more information in the [Substrate documentation](https://docs.substrate.io/v3/concepts/extrinsics/).

**Inherents** contain information that is not provably true, but validators agree on based on some measure of reasonability. For example, a timestamp cannot be proved, but validators can agree that it is within some delta of their system clock. Inherents are not gossiped on the network, and only block authors insert them into blocks.

Signed transactions contain a signature of the account that issued the transaction and stands to pay a fee to have the transaction included on chain. Because the value of including signed transactions on-chain can be recognized prior to execution, they can be gossiped on the network between nodes with a low risk of spam. Signed transactions fit the concept of a transaction in Ethereum or Bitcoin.

Some transactions cannot be signed by a fee-paying account and use unsigned transactions. For example, when a user claims their CHER from the Polygon-Cherry Interoperability Channel to a new CHER address, the new address doesn't yet have any funds with which to pay fees.

#### Transaction Mortality[​](https://wiki.polkadot.network/docs/build-protocol-info#transaction-mortality) <a href="#transaction-mortality" id="transaction-mortality"></a>

Extrinsics can be mortal or immortal. The transaction payload includes a block number and block hash checkpoint from which a transaction is valid and a validity period (also called "era" in some places) that represents the number of blocks after the checkpoint for which the transaction is valid. If the extrinsic is not included in a block within this validity window, it will be discarded from the transaction queue.

The chain only stores a limited number of prior block hashes as reference. You can query this parameter, called `BlockHashCount`, from the chain state or metadata. This parameter is set to 2400 blocks (about four hours) at genesis. If the validity period is larger than the number of blocks stored on-chain, then the transaction will only be valid as long as there is a block to check it against, i.e. the minimum value of validity period and block hash count.

Setting the block checkpoint to zero, using the genesis hash, and a validity period of zero will make the transaction "immortal".

**NOTE:** If an account is reaped and a user re-funds the account, then they could replay an immortal transaction. Always default to using a mortal extrinsic.

#### Unique Identifiers for Extrinsics[​](https://wiki.polkadot.network/docs/build-protocol-info#unique-identifiers-for-extrinsics) <a href="#unique-identifiers-for-extrinsics" id="unique-identifiers-for-extrinsics"></a>

> Note: The assumption that a transaction's hash is a unique identifier is the number one mistake that indexing services and custodians make. This error will cause major issues for your users. Make sure that you read this section carefully.

Many infrastructure providers on existing blockchains, e.g. Ethereum, consider a transaction's hash as a unique identifier. In Substrate-based chains like Cherry, a transaction's hash only serves as a fingerprint of the information within a transaction, and there are times when two transactions with the same hash are both valid. In the case that one is invalid, the network properly handles the transaction and does not charge a transaction fee to the sender nor consider the transaction in the block's fullness.

Imagine this contrived example with a [reaped account](https://wiki.polkadot.network/docs/build-protocol-info#existential-deposit). The first and last transactions are identical, and both valid.

| Index | Hash | Origin    | Nonce | Call                 | Results                       |
| :---: | :--: | --------- | :---: | -------------------- | ----------------------------- |
|   0   | 0x01 | Account A |   0   | Transfer 5 CHER to B | Account A reaped              |
|   1   | 0x02 | Account B |   4   | Transfer 7 CHER to A | Account A created (nonce = 0) |
|   2   | 0x01 | Account A |   0   | Transfer 5 CHER to B | Successful transaction        |

In addition, not every extrinsic in a Substrate-based chain comes from an account as a public/private key pair; Substrate, rather, has the concept of dispatch “origin”, which could be created from a public key account, but could also form from other means such as governance. These origins do not have a nonce associated with them the way that an account does. For example, governance might dispatch the same call with the same arguments multiple times, like “increase the validator set by 10%.” This dispatch information (and therefore its hash) would be the same, and the hash would be a reliable representative of the call, but its execution would have different effects depending on the chain’s state at the time of dispatch.

The correct way to uniquely identify an extrinsic on a Substrate-based chain is to use the block ID (height or hash) and the extrinsic's index. Substrate defines a block as a header and an array of extrinsics; therefore, an index in the array at a canonical height will always uniquely identify a transaction. This methodology is reflected in the Substrate codebase itself, for example to [reference a previous transaction](https://docs.substrate.io/rustdocs/latest/pallet\_multisig/struct.Timepoint.html) from the Multisig pallet.

#### Events[​](https://wiki.polkadot.network/docs/build-protocol-info#events) <a href="#events" id="events"></a>

While extrinsics represent information from the outside world, events represent information from the chain. Extrinsics can trigger events. For example, the Staking pallet emits a `Reward` event when claiming staking rewards to tell the user how much the account was credited.

If you want to monitor deposits into an address, keep in mind that several transactions can initiate a balance transfer (such as `balances.transferKeepAlive` and a `utility.batch` transaction with a transfer inside of it). Only monitoring `balances.transfer` transactions will not be sufficient. Make sure that you monitor events in each block for events that contain your addresses of interest. Monitor events instead of transaction names to ensure that you can properly credit deposits.

#### Fees[​](https://wiki.polkadot.network/docs/build-protocol-info#fees) <a href="#fees" id="fees"></a>

Cherry uses weight-based fees that, unlike gas, are charged _pre-dispatch._ Users can also add a "tip" to increase transaction priority during congested periods. See the [transaction fee](https://wiki.polkadot.network/docs/learn-transaction-fees) page for more info.

#### Encoding[​](https://wiki.polkadot.network/docs/build-protocol-info#encoding) <a href="#encoding" id="encoding"></a>

Parity's integration tools should allow you to deal with decoded data. If you'd like to bypass them and interact directly with the chain data or implement your own codec, Polkadot encodes block and transaction data using the [SCALE codec](https://docs.substrate.io/v3/advanced/scale-codec/).

### Runtime Upgrades[​](https://wiki.polkadot.network/docs/build-protocol-info#runtime-upgrades) <a href="#runtime-upgrades" id="runtime-upgrades"></a>

[Runtime upgrades](https://wiki.polkadot.network/docs/learn-runtime-upgrades) allow Cherry to change the logic of the chain without the need for a hard fork. A hard fork would require node operators to manually upgrade their nodes to the latest runtime version. In a distributed system, this is a complex process to coordinate and communicate. Cherry can upgrade without a hard fork. The existing runtime logic is followed to update the Wasm runtime stored on the blockchain to a new version. The upgrade is then included in the blockchain itself, meaning that all the nodes on the network execute it.

Generally there is no need to upgrade your nodes manually before the runtime upgrade as they will automatically start to follow the new logic of the chain. Nodes only need to be updated when the runtime requires new host functions or there is a change in networking or consensus.

Transactions constructed for a given runtime version will not work on later versions. Therefore, a transaction constructed based on a runtime version will not be valid in later runtime versions. If you don't think you can submit a transaction before the upgrade, it is better to wait and construct it after the upgrade takes place.

Although upgrading your nodes is generally not necessary to follow an upgrade, we recommend following the Polkadot releases and upgrading in a timely manner, especially for high priority or critical releases.

## Other Frequently Asked Questions[​](https://wiki.polkadot.network/docs/build-protocol-info#other-faq) <a href="#other-faq" id="other-faq"></a>

**Can an account's balance change without a corresponding, on-chain transaction?**

No, but not all balance changes are in a _transaction,_ some are in _events._ You will need to run an archive node and listen for events and transactions to track all account activity. This especially applies to _locking_ operations if you are calculating balance as the spendable balance, i.e. free balance minus the maximum lock.

**What chain depth is considered "safe"?**

Cherry uses a deterministic finality mechanism. Once a block is finalized, it cannot be reverted except by a hard fork. Using a finalized depth of ten blocks should be safe.

Note that block production and finality are isolated processes in Cherry, and the chain can have a long unfinalized head.

**Do users need to interact with any smart contracts?**

No, users interact directly with the chain's logic.

**Does Cherry have state rent?**

No, Cherry uses the existential deposit to prevent dust accounts and other economic mechanisms like locking or reserving tokens for operations that utilize state.

**What is an external source to see the current chain height?**

* [Cherry.place blockchain UI](https://cherry.place)
