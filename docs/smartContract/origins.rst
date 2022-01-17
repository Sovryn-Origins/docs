Sovryn Origins
++++++++++++++

OriginsStorage
==============

A contract with all the storage of `OriginsBase`. Basically acts as the harddisk of the system.

OriginsAdmin
============

A basic contract with currently two main roles:

- Owner
- Verifier

An owner has the right on major decision making functions. The owner has too many rights, including the withdrawal of proceedings, thus it is recommended to use a multisig for the same.

A Verifier currently has the right to add any address as verified. To make someone a verifier, owner should call the `addVerifier` function in OriginsAdmin.

OriginsEvents
=============

A contract with all the events of `OriginsBase` listed in it.

OriginsBase
===========

This is the main contract which does all the major works. Each sale is a Tier. And a single contract will be enough to do multiple sales of a unique Token.

The proceedings of the raised amount could be taken by the owner or a pre-set deposit address.

Tier creation could be done with a single function call, or can be done by multiple calls. Individual Tier parameters can be edited as well based on Tier ID.

NOTE: Currently, tier deposit metrics are not set while creating Tier. So, to set those, need to call the `setTierDeposit` function call.

Verification of participants can be done in different mechanism. The different types are:

* `None` - The type is not set, so no one is approved for sale.
* `Everyone` - This type is set to allow everyone.
* `ByAddress` - This type is set to allow only verified addresses.
* `ByStake` - This type is set to allow only addresses with minimum stake requirement.

In the future, new verification types like by vesting, by a combination of stake and/or vest and even by NFTs can be developed.

Sale time is also dependent on two different methods mainly, one is duration (calculated from the start time) or the end timestamp itself. Another method is until supply last as well.

Deposit asset can be either RBTC or any other ERC20 Compliant Token as well, and it can be unique for each tier also.

Transfer Type can be:

* `None` - Transfer hasn't set yet. This is default.
* `Unlocked` - Tokens are unlocked immediately
* `WaitedUnlock` - which means the unlock will happen after a certain period
* `Locked` - which means the tokens will be a linear vesting
* `Vested` - which is tokens vested linearly, but the difference being the voting power in Governance.

The current version only support None, Unlocked, Waited Unlock and Vested for now. Locked will be developed soon.

The contract also keeps track of participating wallets per tier, the number of tokens sold per tier, etc.