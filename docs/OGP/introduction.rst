Origins Governance Proposal
+++++++++++++++++++++++++++

An Origins Governance Proposal, or "OGP", is a document that details a change to the management, allocation, or use of shared resources owned or directly influenced by Origins. All OGPs SHOULD be consistent with the requirements outlined in this document. The OGP author is responsible for building consensus within the community for their OGP and documenting dissenting opinions.

.. note::
    Source: https://github.com/Sovryn-Origins/OGPs/blob/main/README.md

Purpose
=======
The purpose of the Origins Governance Proposal Process ("the OGP process") is to provide a structured process for making changes to the shared resources of Origins. For these shared resources, a governance process is needed to grant or deny access and approve or reject proposed changes. By creating a fair, lightweight, and transparent governance process, the authors of this process hope to give OG holders a meaningful say in the governance of Origins and increase the chances of Origins's success.

Proposal workflow
=================
Parties directly involved in the process are the *OGP author(s)* (you), *Origins Voters*, *Origins Guardians*, and *OGP Editors*. Each of these roles is explained later in this document.

Proposals SHOULD follow this workflow:

* Stage I: Select OGP Track  
* Stage II: Pre-proposal  
* Stage III: Draft Proposal  
* Stage IV: Review Periods  
* Stage V: Bitocracy Vote  

.. note::
    A proposal is NOT REQUIRED to go through Stages I-IV before it is submitted for a Origins Vote in Stage V. However it is strongly RECOMMENDED to follow this whole process so that the proposal gets a proper review and is not perceived with suspicion or hostility by Origins Voters. If a proposal is urgent, it MAY go through an accelerated review process if needed; if you feel your proposal is urgent, to align expectations you SHOULD make this urgency and the reason for urgency known when you introduce your proposal to the community.

Stage I: Select OGP Track
-------------------------
Before you spend time working on a proposal, you SHOULD make sure the proposal complies with this process and has a chance of passing review by your peers. Review the OGP tracks and their requirements, then select the track that you think is best for your proposal. If your proposal meets the requirements, it has a much greater chance of being approved by Origins Voters.

There are five tracks that a OGP can be categorized into. Select the one you think is best for your OGP:

* Contract: proposals for modifying the source code of one or more Origins smart contracts
* Parameter: proposals for modifying one or more parameters on one or more Origins smart contracts
* Proclamation: proposals for making a public statement on behalf of Origins
* Treasury: proposals for transferring funds from the Origins Treasury
* Project: proposals for announcing a new project listing in Origins Platform

A proposal may be categorized as “Other” until a new, appropriate track is approved as part of a Meta OGP.

Each track has its own requirements for OGPs as follows:

Contract
~~~~~~~~
Proposals made to the Contract track SHOULD change one or more of the Origins smart contracts. The proposal SHOULD link to the existing contract(s) to be modified and to the source code of the proposed contract modification(s). All Contract track proposals SHOULD include a link to a third party audit report of the specified modification(s).

* All code modifications and associated documentation introduced by a Contract track proposal SHOULD be published under an MIT license.

Parameter  
~~~~~~~~~
Proposals made to the Parameter track SHOULD change one or more of the Origins smart contract parameters. The proposal SHOULD include information about both the current parameter (if any) and the proposed change to the parameter. All Parameter track proposals MAY include a link to an analysis of the specified parameter change(s).

* All parameter modifications and associated documentation introduced by a Parameter track proposal SHOULD be published under the same license as the smart contract on which the parameter is being modified.

Proclamation
~~~~~~~~~~~~
Proposals made to the Proclamation track SHOULD be used to make a statement on behalf of Origins and can say whatever the author(s) want.

* For example, a Proclamation can be used to signal the Origins community's support for or disapproval of a certain RSKIP.

Treasury  
~~~~~~~~
Proposals made to the Treasury track SHOULD affect the movement of assets held by the Origins Treasury.

* All code, documentation, and content funded by a Treasury track proposal SHOULD be released under one of the following appropriate licenses:  
  * Creative Commons Zero (CC-0)  
  * MIT

Project  
~~~~~~~
Proposals made to the Project track SHOULD be used to make an announcement on behalf of the Project interested to be listed in the Origins Platform, and can say whatever the author(s) want. It should contain the basic details of the project, tokenomics, sale details, milestones, listing fee, etc.

Stage II: Pre-proposal
----------------------
During Stage II you SHOULD seek feedback on your OGP idea by sharing it with your peers in the Origins community and soliciting their feedback. Examples of appropriate venues to share your OGP idea include:

* The `#bitocracy <https://discord.gg/SQvhMVfHka>`_ channel in the Origins Discord
* The `OGP category <ADD OGP CATEGORY FORUM LINK>`_ in the Origins forum  
* The Issues section of the OGPs repo

Be open-minded and respectful of all feedback you receive. Adjust your proposal to address legitimate concerns as they come up to increase the odds of your proposal passing review in later stages.

Stage III: Draft
----------------
After you have asked the Origins community whether an idea has any chance of support, and you have received sufficient feedback to feel confident going forward, you SHOULD create a draft OGP as a draft pull request to the OGPs repo. Draft OGP files submitted to GitHub SHOULD be located in the `OGPs` directory and given a temporary name e.g. `OGP-XX.md`, which the OGP Editor will later assign an OGP number, and SHOULD comply with the requirements set forth below to maintain consistency between OGPs.

* A OGP MAY be drafted and submitted from anywhere. The OGPs repo is used only as a matter of convenience and to ease coordination between Origins contributors.

Stage IV: Review Periods
------------------------
After a OGP has been submitted as a draft pull request to the OGPs repo, it SHOULD undergo three review periods:

1. A Community Review, which starts the moment that a proposal has been submitted to the OGPs repo and lasts for one calendar week.  
2. An Editor Review, which starts when the Community Review ends and lasts for an indefinite period of time.  
3. A Final Review, which starts when the Editor Review ends and lasts for one calendar week.  

Community Review
~~~~~~~~~~~~~~~~
During the Community Review period, the OGP author will have a chance to respond to feedback and make changes to their proposal based on the feedback they have received to increase the likelihood of the proposal passing.

Editor Review
~~~~~~~~~~~~~
At the end of the Community Review period, OGP Editors will perform their review of the proposal. The OGP author SHOULD incorporate any changes suggested by the OGP Editor to prepare the proposal for the Final Review. After a proposal is reviewed by OGP Editors, an OGP Editor will ask the author if the proposal is ready for the Final Review. If the OGP Editors do not receive a response from the OGP author then the OGP Editors may at their discretion either close the pull request or move the proposal on for a Final Review.

* If agreeable, an OGP Editor will assign the OGP a number (generally the number of the OGP pull request), change the status of the OGP pull request from "draft" to "ready", and move the OGP on for a Final Review.  
* Reasons for denying an OGP number and closing the pull request include the OGP being too unfocused, too broad, duplication of effort, being technically unsound, not providing proper motivation or addressing legitimate concerns by reviewers, or not in compliance with this process.  

Final Review
~~~~~~~~~~~~
During the Final Review, the proposal SHOULD NOT be changed. This gives Origins Voters a chance to review the proposal in its final state before the OGP is voted on.

Stage V: Bitocracy Vote
-----------------------
After a OGP has gone through its Final Review, a OGP Editor will add a "Ready to vote" tag to the pull request. At the soonest available opportunity, Origins Guardians will review proposals that have the "Ready to vote" tag and decide whether or not they will veto the proposal.

Once a proposal has been tagged "Ready to vote", the OGP author MAY submit the proposal to Bitocracy for a vote by Origins Voters. Anyone else MAY submit the proposal instead but they SHOULD make an effort to communicate with the OGP author first to make sure the proposal is ready to be submitted and will not be accidentally submitted multiple times.

The vote description submitted for a Origins Vote SHOULD include a link to the specific commit of the proposal being voted on as well as the SHA-256 hash of the raw text file of the proposal.

* Example vote description: `SIP-2: Issuance of cSOV to community members. Details: https://github.com/DistributedCollective/SIPS/blob/00979e4d3b36e18b05f8088607809d8de03e261c/SIP-0002.md (SHA-256: 322cace15ffca9111b5fe1f3ce96ab54302144122c928489813926d33e0270f5)`

Roles in the OGP process
========================

OGP Editors
-----------
OGP Editors are appointed by the owner of the OGPs repo. If the owner of the OGPs repo becomes hostile or unresponsive toward contributors then a new repo can be set up with new OGP Editors, and proposal activity can continue there.

OGP Editors have two responsibilities:

* Review OGPs during the Editor Review and prepare them for the Final Review  
* Update the OGP status and merge pull request

Review proposals  
~~~~~~~~~~~~~~~~
OGP Editors SHOULD review proposals and request modifications to them based on formatting and legibility. OGP Editors MAY close OGP pull requests due to inactivity.

Update the OGP status  
~~~~~~~~~~~~~~~~~~~~~
From the Final Review until the end of the Origins Vote, OGP Editors SHOULD update the OGP pull request and any associated pull requests as specified throughout this document.  

Origins Guardians
-----------------
Origins Guardians are core contributors of Origins to protect the protocol against malicious proposals. The Origins Bitocracy Guardian, i.e. Sovryn Bitocracy has the exclusive authority to veto onchain proposals submitted to the Origins Governance contract.

Origins Voters
--------------
Origins Voters are holders of the OG token who have staked their OG in the Origins Staking contract. The voting power of Origins Voters is determined by the number of OG they have staked and the length of time their OG is staked for. More information about how voting power is calculated can be found `here <https://docs.origins.xyz/en/latest/governance/about.html>`_ Origins Voters can find more information about staking and how to vote on OGPs `here. <https://docs.origins.xyz/en/latest/governance/stakingVesting.html>`_
