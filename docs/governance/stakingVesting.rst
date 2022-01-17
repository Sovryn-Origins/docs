Staking & Vesting
+++++++++++++++++

Governance on Sovryn Origins
============================
TODO

Governance on other launchpads
------------------------------
TODO

The OG Token
------------
OG is an ERC-20 token `minted on RSK <https://explorer.rsk.co/address/TODO_ADD_TOKEN_ADDRESS_HERE>`_. OG itself does not grant governance rights. Instead, OG gives the option for the token holder to stake in the Sovryn Origins protocol, which then provides the token holder with governance rights.

OG is not an "altcoin," i.e., a cryptocurrency alternative to BTC. The purpose of OG is to provide a pseudonymous, censorship-resistant mechanism for governing the parameters of the Sovryn Origins DAO while aligning the incentives of protocol governors with the long-term success of the protocol.

Bitocracy
---------
A Bitocracy is an evolved form of a Vetocracy, which is a governance system where no single entity can make decisions or changes to the system. A modern example of a Vetocracy would be the United Nations, which gives each member nation the right to veto. But this type of governance has its limitations since any one nation can override a majority. Vetocracies are often the result of an inherent lack of trust among the participants and an unwillingness for any of the members to forego sovereignty.

Sovryn Origins's bitcoin-native mode of governance is more of a Bitocracy, which gives weighted voting rights to participants based on how much skin in the game they have while aligning the incentives of all participants. Only users who stake OG ("stakers") receive voting power and they can stake up to a three-year period, during which OG liquidity is suspended, thus removing arbitrage opportunities that could lead to abuses of the system. A Bitocracy encompasses a self-governing, decentralized platform where users interact with the blockchain with complete financial sovereignty, enjoying bitcoin-class security and long-term incentives to act in beneficial ways towards the DAO.

Bitocracy in Action
-------------------
Qualified stakers lead the Sovryn Origins DAO. The difference from other DeFi protocols is that instead of focusing on a highly decentralized governance model where the more, the merrier, Bitocracy values qualified governance involving participants with skin in the game. At any time, Bitocracy participants may choose to take action to improve or expand the protocol, such as modifying a smart contract, issuing a grant, initiating a bounty, etc. All of these changes would be voted on by the community in a series of steps:

* Participant(s) make a proposal in code.
* Stakers vote on the proposal.
* If the proposal is approved, then an execution delay begins. If anyone disagrees strongly with the proposal, then they have this time to walk away before the proposal is executed.

In this system, all staked SOV represents a voice in Bitocracy, but users also have a way to unilaterally exit if they're unhappy with the direction the protocol is taking. Stakers can exit before the end of their staking duration, but they are charged a fee. The more time there is left on their staking duration at the time the staker exits, the higher the penalty, incentivizing them to stay for the full duration. You can find the table of unstaking penalties :ref:`here <Early Unstaking Penalty>`.

By creating the right set of incentives to promote good governance and minimize threats, Sovryn Origins sets its sights on the long-term viability of a bitcoin-native launchpad platform. The Bitocracy model ensures that Sovryn Origins can remain a self-sustaining DeFi platform while granting each user full financial sovereignty.

Staking
=======
Stake for voting power
----------------------
To gain voting power, OG holders must stake their OG for a given period of time. Sovryn Origins uses a quadratic equation with a mapping system to measure the total amount of tokens that are unstaked on any given day. This enables the protocol to compute the voting power of all the tokens staked up to a given point in time. Staking OG for voting power is a feature that is permissionless and openly available to anyone. You can read more about the technical details of staking and how voting power is calculated :ref:`here <Calculating voting weight and voting power>`.

Stake for rewards
-----------------
Aside from Bitocracy participation, there's a financially-rewarding reason for staking OG. Token holders who stake their OG receive staking rewards proportional to their share of the total voting power. For example, a staker with 1% of the voting power will receive 1% of the staking rewards. These staking rewards are earned as a pro-rata share of the platform's revenue. This gives OG holders the ability to earn passive revenue from their staked OG.

How to Stake
------------
TODO

Voting
======
The governance of Sovryn Origins depends heavily on the OG stakeholders exercising their right to vote. It is important to understand what you are voting on fully. For that reason, Sovryn Origins produces OGPs (Origins Governance Proposals) as informational explainers detailing the proposals in the upcoming vote. Examples of past OGPs can be found `here <https://github.com/Sovryn-Origins/OGPs>`_.

As a community-driven project, your vote matters. As an OG stakeholder, it's your voice and your right. You truly make a difference in the development and direction of Sovryn Origins.

Here are just a few of the many reasons why you should vote:

* OGPs have consequences. Each and every OGP is of significant importance, which is why they require a community vote to pass. As a stakeholder, you have the ability to participate in the direction of Sovryn Origins, not just for yourself but for the entire community. Voting enables you to take a stand for the issues you care about. You are an integral part of this project: exercise your right to help decide what's best.
* Not voting is giving up your voice. The direction of the Sovryn project is decided by the people who vote. If you don't vote, others make the decisions for you. Your vote is your voice.
* Your OG is your asset. Voting is your chance to decide how OG is utilized, allocated, and distributed.
* Voting is an opportunity for change. It gives you the ability to make a positive impact. Support the measures and proposals that you feel help the Sovryn Origins community, and oppose the ones you feel strongly against. The objective is to move the project forward for the greater good. Do your part, make your voice heard!
* The Sovryn Origins community depends on you! It is made up of people from all walks of life, from all corners of the world. Some may not value the importance of voting, while others may not fully appreciate the privilege: In that sense, when you vote, you do so not only for yourself but for the benefit of others as well.

How to Vote
-----------
TODO

Delegation
==========
The Sovryn Origins Bitocracy smart contracts support a feature called delegation that enables stakers to delegate their voting power to another address. Importantly, the address that voting power is delegated to DOES NOT gain the ability to unstake or transfer the OG in the original address; the delegate address ONLY can submit and vote on Bitocracy proposals using that voting power.

Why Delegate?
-------------
Delegation is useful for two main purposes:

1. You want to keep your OG transfer authority on one address and voting power on another address. For example, you could keep the private keys with transfer authority in a cold storage address that takes a lot of time and effort to access and maintain the voting power on an address you can easily access from your mobile or desktop wallet.
2. You want to delegate your voting power to a third party for some reason, either temporarily or long-term. For example, if a community member wants to submit a proposal that you support but does not by themselves have enough voting power to submit the proposal, then you and other stakers who support the proposal could temporarily delegate voting power to the community member so they will have enough voting power to submit their proposal. Another example is if you want to delegate your voting power to someone who you consider an expert on the Sovryn protocol, who you think will be a good governor of the system, then you can delegate your voting power long term until you want to either take back your delegation or delegate your voting power to someone else.

How to Delegate
---------------
TODO

Revoke your delegated vote
--------------------------
To revoke your delegated voting power from an address and return the voting power back to your own address, repeat the same process to delegate your voting power, and simply enter your own address as the address that you want to delegate your voting power to. Once the delegation is confirmed, your voting power will be transferred from the previous delegate address to your own delegate address.

Become a Bitocracy Delegate
---------------------------
Visit the `Delegates subcategory <TODO_ADD_FORUM_LINK>`_ in the Sovryn Forum to learn more about how you can become a delegate in the Sovryn Origins Bitocracy.