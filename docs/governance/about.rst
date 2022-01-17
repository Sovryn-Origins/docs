About
+++++

Overview
========

Sovryn Origins is a smart contract system built on RSK. The Sovryn Origins smart contracts have many parameters that can be modified, and the smart contracts themselves can also be modified. This raises the issue of governance: what the parameters and smart contracts of the Sovryn Origins smart contract system are that can be governed, what the processes are for modifying these parameters and smart contracts, and how to modify the governance process itself.

.. note::
    This page intends to describe how Sovryn Origins governance currently works at a medium level of detail. While this page may not have all of the information about Sovryn Origins governance, we have strived to ensure that the information that is here is 100% accurate. We welcome feedback with any additions or corrections to this content.

    For the canonical description of Sovryn Origins governance, you will have to find and read the source code of the relevant smart contracts in their current state on the RSK blockchain.

System Contracts, Parameter and their owners
============================================

TODO

Governance Contracts and their settings
=======================================

Governor is an instance of GovernorAlpha. The mainnet address of Governor (instance of GovernorAlpha) is: TODO

Governor
--------

 | Voting Token: OG (TODO)
 | Quorum: >5%
 | Support: >50%
 | Min. Proposal Stake: 1%
 | Execution delay: Time Lock
 | Vote duration: 2880 blocks (approx. 1 day)
 | Contract call limit: 10 calls
 | Guardian: Sovryn Governor Owner (``0x6496df39d000478a7a7352c01e0e713835051ccd``)

Time Lock
---------

 | 3 days
 | Min 3 hours
 | Max 30 days
 | Grace period: 2 weeks

Staking Details
---------------

 | Staking period length: Two weeks, repeating bi-weekly starting from SOV TGE
 | Voting weight equation: :math:`f(x)=V*({m^{2}}-{x^{2}})/{m^{2}}+1`
 | Voting power equation: :math:`VP(x) = f(x) * s`

Staking Overview
~~~~~~~~~~~~~~~~

SOV holders must stake their SOV to gain voting power in Bitocracy. Voting power is determined using a quadratic formula based on the amount and duration of SOV staked.

Staking periods are divided into bi-weekly intervals, beginning at the time of the SOV token generation event and repeating every two weeks from then on. Users will acquire voting power from their stake and begin their staking duration when the staking period after they started staking begins. Once their staking duration begins, users can withdraw their staked SOV early if they are willing to take a slashing penalty. Users can also delegate their voting power to other addresses.

In addition to earning voting power, SOV holders who stake their SOV become eligible for protocol fee-sharing, receiving a proportional share (as measured by voting power) of all tokens that have been collected in the fee-sharing pool. Tokens collected in the fee-sharing pool come from protocol fees plus all slashed SOV from early unstaking penalties.

Calculating voting weight and voting power
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The stake weighting function is based on a quadratic formula, using the amount and duration of SOV staked.

Let ``m`` be the maximum staking period (1092 days) , ``x`` be the number of days passed since the beginning of the period, and ``V`` be the maximum voting weight (currently 9). The voting weight at a given time ``x`` can be described as:

:math:`f(x)=V*({m^{2}}-{x^{2}})/{m^{2}}+1`

``+1`` is added in the end to shift the weights to lie in :math:`[1, V+1]` instead of :math:`[0, V]`.

Users will usually not stake the maximum duration, so ``x`` has to be computed based on the remaining days until unstaking:

:math:`x = m-RemainingDays`

The user's voting power ``VP`` at a given time ``x`` is the product of their stake ``s`` and their voting weight:

:math:`VP(x) = f(x) * s`

The total voting power equals the sum of the voting power of all users. However, since we can't iterate over an array with unlimited size, we need to compute it differently. Instead of summing up the user voting powers, we introduce a mapping, which stores the total amount of SOV to be unstaked on a given day, and call it ``stakedUntil``.

Whenever a user stakes SOV, not only is their staking balance updated, but also ``stakedUntil[unstakingDay]``. Whenever a user increases their staking balance, the mapping also needs to be increased. Whenever a user increases their staking time, their stake is subtracted from ``stakedUntil[previousUnstakingDay]`` and added to ``stakedUntil[newUnstakingDay]``.

Now, we can compute the voting power of all SOV staked until a given point in time in a single operation. The daily voting power DVP is given by:

:math:`DVP(x) = f(x) *\sum_{u} s_{u}(x)`

where :math:`\sum_{u}s_{u}(x)` is the content of ``stakedUntil[x]``.

The total voting power can then be computed by summing up the daily voting powers of the next ``m`` days:

:math:`TVP=\sum_{x=0}^{m}*DVP(x)`

This process requires ``m`` iterations. With a maximum staking duration of 3 years, this would cost approximately 1,000,000 gas. In order to save gas costs, we decided to stake in bi-weekly periods instead. As a consequence, voting weights are only adjusted every 2 weeks and we need a maximum of 78 iterations (instead of 1095).

The ``stakedUntil`` mapping needs to be checkpointed to allow the computation of the total voting power for a point of time in the past. The same is true for the user stakes.

Delegating
~~~~~~~~~~

Once their SOV is staked, users are able to delegate their voting power to another address. Users may want to do this if, for example, they are unable to be actively involved in governance and want a more active or qualified individual/group to vote on their behalf, or if they prefer to maintain transfer authority for their SOV on one address but voting authority on a different address.

Given the possibility of delegation, a user can have a potentially large number of addresses delegating voting power to their address, with each of these other addresses staking for different durations. The voting power of a delegatee is computed the same way the total voting power is computed: as a sum of the voting powers per unstaking day.

Early Unstaking Penalty
~~~~~~~~~~~~~~~~~~~~~~~

Users who unstake before the end of their staking duration are subject to a token slashing penalty of up to 30%. This incentivizes users who stake to maintain their commitment to the protocol. Slashing penalties are deducted from the staking balance and sent to the fee-sharing pool and redistributed to all other staked SOV holders.

The penalty chart for early unstaking is as follows:

+-----------------+-------------------------+
| Weeks remaining | Early unstaking penalty |
+=================+=========================+
| 2               | 3.69%                   |
+-----------------+-------------------------+
| 4               | 4.37%                   |
+-----------------+-------------------------+
| 6               | 5.04%                   |
+-----------------+-------------------------+
| 8               | 5.70%                   |
+-----------------+-------------------------+
| 10              | 6.35%                   |
+-----------------+-------------------------+
| 12              | 6.99%                   |
+-----------------+-------------------------+
| 14              | 7.63%                   |
+-----------------+-------------------------+
| 16              | 8.25%                   |
+-----------------+-------------------------+
| 18              | 8.87%                   |
+-----------------+-------------------------+
| 20              | 9.48%                   |
+-----------------+-------------------------+
| 22              | 10.08%                  |
+-----------------+-------------------------+
| 24              | 10.67%                  |
+-----------------+-------------------------+
| 26              | 11.25%                  |
+-----------------+-------------------------+
| 28              | 11.82%                  |
+-----------------+-------------------------+
| 30              | 12.39%                  |
+-----------------+-------------------------+
| 32              | 12.94%                  |
+-----------------+-------------------------+
| 34              | 13.49%                  |
+-----------------+-------------------------+
| 36              | 14.02%                  |
+-----------------+-------------------------+
| 38              | 14.55%                  |
+-----------------+-------------------------+
| 40              | 15.07%                  |
+-----------------+-------------------------+
| 42              | 15.58%                  |
+-----------------+-------------------------+
| 44              | 16.08%                  |
+-----------------+-------------------------+
| 46              | 16.58%                  |
+-----------------+-------------------------+
| 48              | 17.06%                  |
+-----------------+-------------------------+
| 50              | 17.53%                  |
+-----------------+-------------------------+
| 52              | 18.00%                  |
+-----------------+-------------------------+
| 54              | 18.46%                  |
+-----------------+-------------------------+
| 56              | 18.91%                  |
+-----------------+-------------------------+
| 58              | 19.34%                  |
+-----------------+-------------------------+
| 60              | 19.78%                  |
+-----------------+-------------------------+
| 62              | 20.20%                  |
+-----------------+-------------------------+
| 64              | 20.61%                  |
+-----------------+-------------------------+
| 66              | 21.01%                  |
+-----------------+-------------------------+
| 68              | 21.41%                  |
+-----------------+-------------------------+
| 70              | 21.79%                  |
+-----------------+-------------------------+
| 72              | 22.17%                  |
+-----------------+-------------------------+
| 74              | 22.54%                  |
+-----------------+-------------------------+
| 76              | 22.90%                  |
+-----------------+-------------------------+
| 78              | 23.25%                  |
+-----------------+-------------------------+
| 80              | 23.59%                  |
+-----------------+-------------------------+
| 82              | 23.92%                  |
+-----------------+-------------------------+
| 84              | 24.25%                  |
+-----------------+-------------------------+
| 86              | 24.56%                  |
+-----------------+-------------------------+
| 88              | 24.87%                  |
+-----------------+-------------------------+
| 90              | 25.17%                  |
+-----------------+-------------------------+
| 92              | 25.46%                  |
+-----------------+-------------------------+
| 94              | 25.74%                  |
+-----------------+-------------------------+
| 96              | 26.01%                  |
+-----------------+-------------------------+
| 98              | 26.27%                  |
+-----------------+-------------------------+
| 100             | 26.52%                  |
+-----------------+-------------------------+
| 102             | 26.76%                  |
+-----------------+-------------------------+
| 104             | 27.00%                  |
+-----------------+-------------------------+
| 106             | 27.23%                  |
+-----------------+-------------------------+
| 108             | 27.44%                  |
+-----------------+-------------------------+
| 110             | 27.65%                  |
+-----------------+-------------------------+
| 112             | 27.85%                  |
+-----------------+-------------------------+
| 114             | 28.04%                  |
+-----------------+-------------------------+
| 116             | 28.22%                  |
+-----------------+-------------------------+
| 118             | 28.40%                  |
+-----------------+-------------------------+
| 120             | 28.56%                  |
+-----------------+-------------------------+
| 122             | 28.72%                  |
+-----------------+-------------------------+
| 124             | 28.86%                  |
+-----------------+-------------------------+
| 126             | 29.00%                  |
+-----------------+-------------------------+
| 128             | 29.13%                  |
+-----------------+-------------------------+
| 130             | 29.25%                  |
+-----------------+-------------------------+
| 132             | 29.36%                  |
+-----------------+-------------------------+
| 134             | 29.46%                  |
+-----------------+-------------------------+
| 136             | 29.56%                  |
+-----------------+-------------------------+
| 138             | 29.64%                  |
+-----------------+-------------------------+
| 140             | 29.72%                  |
+-----------------+-------------------------+
| 142             | 29.78%                  |
+-----------------+-------------------------+
| 144             | 29.84%                  |
+-----------------+-------------------------+
| 146             | 29.89%                  |
+-----------------+-------------------------+
| 148             | 29.93%                  |
+-----------------+-------------------------+
| 150             | 29.96%                  |
+-----------------+-------------------------+
| 152             | 29.98%                  |
+-----------------+-------------------------+
| 154             | 30.00%                  |
+-----------------+-------------------------+
| 156             | 30.00%                  |
+-----------------+-------------------------+