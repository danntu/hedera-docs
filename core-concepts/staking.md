# Staking

The Hedera public ledger uses a proof-of-stake consensus mechanism, in which each node’s influence on consensus is proportional to the amount of cryptocurrency it has staked to it. A transaction is validated and placed into consensus after it is validated by nodes representing an aggregate stake of over two thirds of the network’s total number of hbars (the number of hbars is fixed at 50 billion). Stake is expressed as an amount in hbars. It is important to ensure that most of the cryptocurrency is actually being staked, so that the network continues to run. This information can be referenced from the latest Hedera [whitepaper](https://hedera.com/hh\_whitepaper\_v2.1-20200815.pdf).

The staking feature will be rolled out in four phases; the first two phases are described below; the final two phases will be made available at the start of Phase I.

**Phase I: Technical Availability \[Complete]**

The staking functionality is now available and live on both the Hedera testnet and mainnet, as of July 21, 2022. In phase I, users will technically be able to stake their account to mainnet nodes but this will not contribute to a node’s consensus weight (voting power). This initial technical availability release does not reward participants for staking, but enables a level playing field whereby all market participants have the possibility to join the staking program, and avoids giving an unfair advantage to the first few who stake.

**Phase II: Ecosystem Development  \[Complete]**

During this phase, supported exchanges and wallets will be able to integrate the staking functionality to provide account holders an easy way to stake their hbars, but will not distribute rewards. In addition, web applications for delegating stake will likely be built for utilization by the retail ecosystem. During this phase, there will be visibility of stake per node, and staking to a node will affect its consensus weight (voting power) with monthly updates.

#### **Phase III: Staking Rewards Program Launch \[Complete]**

The Hedera Governing Council will determine when the Hedera ecosystem has reached a minimum viable set of integrations to enable staking rewards. Once this is determined, the council (through CoinCom) will vote to update the reward rate, and subsequently, the mainnet will be updated with the agreed-upon reward rate. The staking reward rate voted on by CoinComm is 1 billion hbars/year. \
\
Once updated, the staking reward account (0.0.800) will be eligible to distribute rewards earned by stakers, once the rewards threshold of 250M total hbars has been met. Rewards will continue to be distributed even if, after this time, the balance of account 0.0.800 goes below 250M.

#### Phase IV: Complete Staking Implementation

In this phase, 24-hour updates for visibility into stake per node and the node uptime feature will be released. This means that instead of updating node stake visibility on a monthly basis, node stake visibility will be updated on a 24-hour epoch interval. When the uptime feature takes effect, staked accounts will not earn rewards when nodes are unable to participate in consensus (unavailable or offline).

### **Staking Nodes**

{% hint style="info" %}
The Hedera Governing Council voted to change the min stake value from half of the max node stake value to 1/4 of the max node stake value.
{% endhint %}

All consensus nodes run by the Hedera Governing Council participate in distributing rewards to the accounts that are staked to them. You can find information about each node in the network by visiting one of the Hedera network explorers or getting the network [address book](../docs/mirror-node-api/rest-api.md#api-v1-network-nodes). In the future, network participation will open up to community nodes and eventually to the public as part of Hedera’s decentralization efforts.

Nodes have a **minimum stake** and **maximum stake**. The node's minimum stake must be met for the accounts staked to that node to be eligible to earn staking rewards. Staked tokens that go over the maximum stake will no longer impact the proportion of rewards returned. The maximum stake threshold for each node will be the total number of hbars divided by the total number of nodes in the network. The minimum node stake threshold value will be 1/4 of the maximum node stake value. These values will change as more nodes are added to the network or can change by vote of the Hedera Governing Council.

Example:

Minimum Stake: ​50,000,000,000 hbars\*(1/26nodes)\*(1/4)

Maximum Stake: ​50,000,000,000 hbars\*(1/26nodes)

### **Lockup Period**

There is **no lock-up period** when accounts are staked to a node. Stakers do not need to choose an amount of hbars to stake from their account. The entire balance of the account is staked automatically to the selected node or account. There is no concept of “bonding” or “slashing” of your tokens. The staked account balance is liquid at all times.

### **Staking Reward Account**

The staking reward account is the account that will distribute rewards to the eligible staked accounts. The staking reward account ID is [0.0.800](https://hashscan.io/#/mainnet/account/0.0.800?type=) on mainnet. Anyone in the community can contribute to the rewards pool by transferring hbars into that account. This account has no keys and therefore any hbars transferred into this account cannot be returned to the owner. If you choose to contribute to the rewards pool, please make sure to double-check your transfer transaction details.

The staking reward account needs to meet a minimum balance before rewards can begin to distribute rewards earned to the eligible staked accounts. The minimum hbar balance threshold for the reward account is 250 million hbars voted on by the Hedera Governing Council. If this balance is not met staking rewards will not be distributed. You can view the balance of this account by visiting any of the Hedera network explorers.

Once the minimum threshold is met, rewards will continue to be distributed to staked accounts as long as there is a balance in the rewards account even if it falls below the initial minimum threshold. The reward rate will initially be set to zero. The Hedera Governing Council will vote and update the reward rate when the Hedera Staking Reward Program goes live.&#x20;

### **Staking Rewards**

The staking reward rate will initially be set to zero in Phase I. The Hedera Governing Council will determine when the Hedera ecosystem has reached a minimum viable set of integrations to enable staking rewards. Once this is determined, the council (through CoinCom) will vote to update the reward rate, and subsequently, the mainnet will be updated with the agreed-upon reward rate.

Any account can elect to stake to a node or another account. The **minimum staking period** is the minimum amount of time an account needs to be staked to a consensus node before the account is eligible to earn rewards. The minimum staking period is **one day (24 hours).** The staking period begins at midnight UTC and the staking period ends at midnight UTC. The staking period is defined by the Hedera Governing Council. The earned rewards are not transferred to the staked account immediately after an account has been staked for one full staking period. Please see the Staking Reward Distribution section for what scenarios trigger the payment of a reward.

Accounts staked for less than the defined minimum staking period are not eligible to earn rewards for that period. Nodes and accounts accumulate stake and rewards per whole hbar. Fractions are rounded down.

In order for a staked account to be eligible to earn rewards the following must be true:

* The staking reward account needs to have met the initial threshold balance of hbars
  * Once the minimum threshold value has been met, the rewards account will continue to reward staked accounts even if the balance falls below the initial threshold
* The account the node is staked to meets the minimum node stake threshold value
* The account needs to be staked for the minimum staking period
* The reward rate is voted on by the Hedera Governing Council and updated on mainnet

Rewards will continue to be earned when a node is down or inactive in the first phase. The Council (through CoinCom) has voted to implement a maximum cap of 6.5% annual reward rate. The actual reward rate will vary depending on how many hbars are staked for rewards, but the rate will not exceed the cap. In the future, when nodes are down or inactive the staked account will not be eligible to earn rewards.

This staking system offers additional unique functionality: **indirect staking**. If account A stakes to node N, then the stake increases the consensus weight of N, and account A is rewarded for every 24-hour period that it stakes. If account A stakes to account B, and account B stakes to node N, then the stake from both A and B will increase the consensus weight of N, but the rewards for both A and B will be received by B.

An account can optionally decline to earn rewards when staked. The account will still be counted towards meeting the node’s minimum stake value.

### **Staking Reward Distribution**

Rewards distributions can be triggered by one of the following mechanisms:

* When your staked account has hbars transferred to it or debited from it
* When you update the staked account to stake to a different node
* When you update the staked account to decline rewards
* When the total number of hbars staked to an account changes
* When the staked account is auto-renewed (auto-renew for accounts is not enabled at this time)
* When an account staked to this one has its account balance change
* You can continue to collect rewards earned up to 365 days without a rewards payment being triggered
  * If you go more than 365 days without a rewards payment, you can only collect on the last 365 days
  * Example: Staker stakes for 1000 days, never collecting a reward, and on the 1001st day collect your rewards
    * You will only get rewards for the latest 365 periods
    * You will not earn rewards for the preceding 635 periods (1,000 days - 365 days)

### Get Started with Staking

Supported Wallets:

* [HashPack](https://www.hashpack.app/post/staking-with-hashpack)
* [Blade](https://www.bladewallet.io/)
* [MyHbarWallet](https://myhbarwallet.com/)
* [Wallawallet ](https://wallawallet.com/2022/07/21/how-to-stake-hbar/)
* [Yamgo](https://yamgo.com/)

Exchanges:

* [OKX](https://www.okx.com/support/hc/en-us/articles/9824479181709-Win-up-to-72-APY-with-Hedera-HBAR-Staking)
