---
description: Learn about Vaults in StakeWise V3
cover: ../.gitbook/assets/Frame 27513376 (1).png
coverY: 0
---

# Vaults

Vaults are isolated staking pools that can process ETH and GNO deposits into staking, distribute rewards and handle withdrawals in a trustless and non-custodial manner.&#x20;

Anyone can deploy a Vault to enable ETH and GNO staking on specific terms, like a bespoke staking fee, unique mix of operators, custom MEV strategy, etc.

ETH and GNO deposits into any Vault can only be used to launch validators for that specific Vault. Any rewards (or penalties) accumulated by these validators will belong to the Vault. This makes every Vault isolated from others, allowing depositors to customize staking experience to their needs.&#x20;

All deposits, rewards distribution, and withdrawals are handled by smart contracts, making staking in Vaults fully non-custodial.

### For stakers

#### Staking and unstaking

{% tabs %}
{% tab title="ETH" %}
**Staking and deposit queue**

Whenever users stake ETH into a particular Vault, that Vault contract accumulates all deposits and launches a new validator for every 32 ETH collected.&#x20;

[<mark style="color:blue;">Read our guide about staking in Vaults -></mark>](../guides/staking.md#staking-with-vaults)

Registering new validators in the Beacon Chain can take several weeks during times when many new staking deposits are being made. ETH staked in a Vault and used to create a validator will not start producing staking rewards until the validator passes the deposit queue and becomes active. This may cause a dilution in Vault's APY.&#x20;

**Rewards reinvestment**

All rewards earned by the Vault's validators are collected in the Vault contract, and are accumulated together with new ETH deposits to launch validators for the Vault. This ensures that all rewards are auto-compounded for a higher Vault APY.&#x20;

**Unbonded ETH**

Amounts less than 32 ETH that are accumulated from new deposits and earned rewards cannot be used for staking and therefore do not earn any rewards. Such ETH is considered unbonded.

High amount of unbonded ETH relative to the Vault's total value of staked ETH can cause a dilution in Vault APY, because ETH rewards are distributed among more ETH than what is actively being used for validation. To optimize for performance, StakeWise may use unbonded ETH to process osETH redemptions and liquidations.&#x20;

[<mark style="color:blue;">Read more about osETH redemptions -></mark>](https://docs.stakewise.io/protocol-overview-in-depth/ostoken#redeemable-for-eth-or-gno)

**Unstaking and exit queue**

Whenever users request to unstake ETH from a particular Vault, the unbonded ETH is used first to process an unstaking request.

If there isn't enough unbonded ETH in the Vault, a sufficient number of Vault validators will be automatically exited to provide enough ETH for unstaking. Since exiting validators from the Beacon Chain takes time, users who requested to unstake their ETH are placed in the exit queue. Once the exit queue is over, users can claim their unstaked ETH whenever they want.&#x20;

Users who requested to unstake ETH from a Vault and were placed into the exit queue will continue earning staking rewards until their ETH has been exited from staking.&#x20;

[<mark style="color:blue;">Read our guide about unstaking ETH from Vaults -></mark>](vaults.md#staking-and-unstaking)
{% endtab %}

{% tab title="GNO" %}
**Staking and deposit queue**

Whenever users stake GNO into a particular Vault, that Vault contract accumulates all deposits and launches a new validator for every 1 GNO collected.&#x20;

[<mark style="color:blue;">Read our guide about staking in Vaults -></mark>](../guides/staking.md#staking-with-vaults)

Registering new validators in the Gnosis Beacon Chain can take several weeks during times when many new staking deposits are being made. GNO staked in a Vault and used to create a validator will not start producing staking rewards until the validator passes the deposit queue and becomes active. This may cause a dilution in Vault's APY.&#x20;

**Rewards reinvestment**

All rewards earned by the Vault's validators are collected in the Vault contract, and are accumulated together with new GNO deposits to launch validators for the Vault. This ensures that all rewards are auto-compounded for a higher Vault APY.&#x20;

**Unbonded GNO**

Amounts less than 1 GNO that are accumulated from new deposits and earned rewards cannot be used for staking and therefore do not earn any rewards. Such GNO is considered unbonded.

High amount of unbonded GNO relative to the Vault's total value of staked GNO can cause a dilution in Vault APY, because GNO rewards are distributed among more GNO than what is actively being used for validation. To optimize for performance, StakeWise may use unbonded GNO to process osGNO redemptions and liquidations.&#x20;

[<mark style="color:blue;">Read more about osGNO redemptions -></mark>](https://docs.stakewise.io/protocol-overview-in-depth/ostoken#redeemable-for-eth-or-gno)

**Unstaking and exit queue**

Whenever users request to unstake GNO from a particular Vault, the unbonded GNO is used first to process an unstaking request.

If there isn't enough unbonded GNO in the Vault, a sufficient number of Vault validators will be automatically exited to provide enough GNO for unstaking. Since exiting validators from the Gnosis Beacon Chain takes time, users who requested to unstake their GNO are placed in the exit queue. Once the exit queue is over, users can claim their unstaked GNO whenever they want.&#x20;

Note that users who requested to unstake GNO from a Vault and were placed into the exit queue stop earning staking rewards as soon as they are placed in the queue.&#x20;

[<mark style="color:blue;">Read our guide about unstaking GNO from Vaults -></mark>](vaults.md#staking-and-unstaking)
{% endtab %}
{% endtabs %}

#### Minting osToken

{% tabs %}
{% tab title="osETH" %}
Stake in any Vault can be made liquid by minting osETH, a liquid staking token. osETH represents ETH staked in Vaults and earns ETH rewards that accrue from their validators.

osETH minting is dependent on the Vault LTV level. Most Vaults can mint osETH for up to 90% of the value of their ETH stake. While certain DAO-approved Vaults are eligible for a 99.99% minting threshold for osETH.&#x20;

99.99% LTV Vaults must meet strict requirements set by the StakeWise DAO to ensure the highest standard of performance. Criteria include:

* having at least 10k ETH staked,&#x20;
* charging a Vault fee of no more than 5%,&#x20;
* consistently ranking above the median performance for all stakers in the network,&#x20;
* using the latest version of Vaults,&#x20;
* and locking 5M SWISE in a DAO-controlled address as a bond (serves as collateral to cover any potential slashing losses).

[<mark style="color:blue;">Read our guide about minting osETH from Vaults -></mark> ](https://docs.stakewise.io/guides/ostoken#minting-ostoken-from-vaults-to-start-liquid-staking)
{% endtab %}

{% tab title="osGNO" %}
Stake in any Vault can be made liquid by minting osGNO, a liquid staking token. osGNO represents GNO staked in Vaults and earns GNO rewards that accrue from their validators.

osGNO minting is dependent on the Vault LTV level. Most Vaults can mint osGNO for up to 90% of the value of their GNO stake. While certain DAO-approved Vaults are eligible for a 99.95% minting threshold for osGNO.&#x20;

99.95% LTV Vaults must meet strict requirements set by the StakeWise DAO to ensure the highest standard of performance. Criteria include:

* having at least 5k GNO staked,&#x20;
* charging a Vault fee of no more than 15%,&#x20;
* consistently ranking above the median performance for all stakers in the network,&#x20;
* using the latest version of Vaults,&#x20;
* and locking 1M SWISE in a DAO-controlled address as a bond (serves as collateral to cover any potential slashing losses).

[<mark style="color:blue;">Read our guide about minting osGNO from Vaults -></mark>](https://docs.stakewise.io/guides/ostoken#minting-ostoken-from-vaults-to-start-liquid-staking)&#x20;
{% endtab %}
{% endtabs %}

#### Vault fee

{% tabs %}
{% tab title="ETH" %}
Every Vault has its own staking fee set by the Vault Admin. This fee is applied to the rewards earned by the Vault, and can range from 0% to 100%. The fee is automatically deducted when rewards are distributed, so the amount of staking rewards users earn is already net of the staking fee.&#x20;

The Vault APY reflects the staking rewards earned by the Vault after the fee has been applied, to make choosing a Vault easier. However, StakeWise advises users to always check the Vault fee before depositing ETH into it to be fully aware of the staking terms.

Note that the Vault Admin cannot change the staking fee once the Vault is registered, so stakers can have peace of mind about staking with Vaults.&#x20;
{% endtab %}

{% tab title="GNO" %}
Every Vault has its own staking fee set by the Vault Admin. This fee is applied to the rewards earned by the Vault, and can range from 0% to 100%. The fee is automatically deducted when rewards are distributed, so the amount of staking rewards users earn is already net of the staking fee.&#x20;

The Vault APY reflects the staking rewards earned by the Vault after the fee has been applied, to make choosing a Vault easier. However, StakeWise advises users to always check the Vault fee before depositing GNO into it to be fully aware of the staking terms.

Note that the Vault Admin cannot change the staking fee once the Vault is registered, so stakers can have a peace of mind about staking with Vaults.&#x20;
{% endtab %}
{% endtabs %}

#### Flow of funds

{% tabs %}
{% tab title="ETH" %}
Every Vault is a staking pool that will:

* accept ETH deposits
* launch validators using deposited ETH
* distribute ETH rewards to stakers in the Vault
* distribute the staking fee to the Vault recipient address
* exit validators to process ETH withdrawals from staking

Throughout its lifecycle, every Vault remains fully non-custodial, meaning that no-one can arbitrarily access or control stakers' funds, including the StakeWise DAO. The flow of funds in and out of staking happens automatically using smart contracts.
{% endtab %}

{% tab title="GNO" %}
Every Vault is a staking pool that will:

* accept GNO deposits
* launch validators using deposited GNO
* distribute GNO rewards to stakers in the Vault
* distribute the staking fee to the Vault recipient address
* exit validators to process GNO withdrawals from staking

Throughout its lifecycle, every Vault remains fully non-custodial, meaning that no-one can arbitrarily access or control stakers' funds, including the StakeWise DAO. The flow of funds in and out of staking happens automatically using smart contracts.&#x20;
{% endtab %}
{% endtabs %}

#### Vault APY formula

{% tabs %}
{% tab title="Formula" %}
The APY of every Vault is calculated using the following formula:&#x20;

{% code overflow="wrap" %}
```
Net Vault APY = average of 14 Vault APY snapshots
```
{% endcode %}

where

{% code overflow="wrap" %}
```
Vault APY snapshot = [(amount of consensus rewards earned by the Vault's validators + amount of execution rewards earned by the Vault's validators - Vault fee) * 365 / 0.5] / Vault TVL at the moment of taking the snapshot
```
{% endcode %}

and a snapshot is taken every \~12 hours.
{% endtab %}
{% endtabs %}

#### Solo Vaults

{% tabs %}
{% tab title="ETH" %}
Solo Vaults are Public or Private Vaults where the Vault Admin is both the node operator and the depositor of ETH in the Vault.&#x20;

Solo Vaults can be configured to a solo staker's liking, including setting the fee to the desired level, choosing between the Smoothing Pool and Own Escrow for handling of MEV, opting for a tokenless Vault to avoid potentially taxable token swaps on deposits / withdrawals, etc.

[<mark style="color:blue;">Read more about configuring a Vault -></mark>](vaults.md#for-operators-of-vaults)
{% endtab %}

{% tab title="GNO" %}
Solo Vaults are Public or Private Vaults where the Vault Admin is both the node operator and the depositor of GNO in the Vault.&#x20;

Solo Vaults can be configured to a solo staker's liking, including setting the fee to the desired level, choosing between the Smoothing Pool and Own Escrow for handling of MEV, opting for a tokenless Vault to avoid potentially taxable token swaps on deposits / withdrawals, etc.

[<mark style="color:blue;">Read more about configuring a Vault -></mark>](vaults.md#for-operators-of-vaults)
{% endtab %}
{% endtabs %}

### For operators of Vaults

#### Vault parameters

{% tabs %}
{% tab title="ETH" %}
Vaults are staking pools with customizable parameters. Some of them are defined at the moment of Vault creation, while others can be changed well into the Vault lifecycle.&#x20;

**Vault type**

Allows Vaults to be Public or Private.&#x20;

Public Vaults can receive staking deposits from any wallet. Private Vaults can only receive deposits from wallets that have been whitelisted by the Vault Admin.

Vault type is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault capacity**

Sets a limit to the total value of ETH that can be deposited into a Vault. Can range from 32 ETH to infinity.&#x20;

Setting/choosing an appropriate Vault capacity helps to ensure that the staking infrastructure of the Vault Operator does not carry more validators than it was designed to handle.&#x20;

Vault capacity is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault fee**

Sets a percentage fee that will be withheld from the rewards earned by Vault's validators as compensation for staking services. Can range from 0 to 100%.

Setting/choosing an appropriate Vault fee helps to ensure that the Vault produces high net APY, remains profitable for the operator and competitive in the Vaults Marketplace.&#x20;

Vault fee is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault token**

Defines whether a Vault has an ERC-20 token to represent ETH staked by users in the Vault, or the Vault is tokenless.

Vaults that opt into having a Vault Token can set its name and symbol (e.g. mntETH), which will be visible in most portfolio tracking applications.&#x20;

Setting/choosing a Vault with Vault Tokens allows users to transfer their stake in the Vault as long as they don't have osETH minted. It also allows Vault owners to develop a utility & liquidity ecosystem for ETH staked in their Vault.&#x20;

Meanwhile, tokenless Vaults protect users from triggering a tax event when depositing or withdrawing ETH from the Vault. A stake in the tokenless Vault cannot be transferred to another wallet.&#x20;

Presence of Vault Tokens is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault block rewards destination**

Allows Vaults to use either a Smoothing Pool or Own Escrow for collecting the block rewards.&#x20;

Using a Smoothing Pool helps achieve a stable Vault APY because block production rewards are shared among all the participating Vaults proportionately to their size. Using Own Escrow preserves the randomness of receiving block production duties and results in a more volatile Vault APY when the Vault has a small number of validators.&#x20;

Block rewards destination is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault branding**

Allows Vault Admin to set the name, description and avatar for their Vault.&#x20;

Vault branding can be changed at any time.&#x20;

**Vault verification**

Vault verification provides certainty to stakers that the Vault branding is accurate, i.e. a Vault branded by Operator A is indeed controlled and run by Operator A. Verification is a manual process managed by the core StakeWise team.&#x20;
{% endtab %}

{% tab title="GNO" %}
Vaults are staking pools with customizable parameters. Some of them are defined at the moment of Vault creation, while others can be changed well into the Vault lifecycle.&#x20;

**Vault type**

Allows Vaults to be Public or Private.&#x20;

Public Vaults can receive staking deposits from any wallet. Private Vaults can only receive deposits from wallets that have been whitelisted by the Vault Admin.

Vault type is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault capacity**

Sets a limit to the total value of GNO that can be deposited into a Vault. Can range from 1 GNO to infinity.&#x20;

Setting/choosing an appropriate Vault capacity helps to ensure that the staking infrastructure of the Vault Operator does not carry more validators than it was designed to handle.&#x20;

Vault capacity is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault fee**

Sets a percentage fee that will be withheld from the rewards earned by Vault's validators as compensation for staking services. Can range from 0 to 100%.

Setting/choosing an appropriate Vault fee helps to ensure that the Vault produces high net APY, remains profitable for the operator and competitive in the Vaults Marketplace.&#x20;

Vault fee is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault token**

Defines whether a Vault has an ERC-20 token to represent GNO staked by users in the Vault, or the Vault is tokenless.

Vaults that opt into having a Vault Token can set its name and symbol (e.g. mntGNO), which will be visible in most portfolio tracking applications.&#x20;

Setting/choosing a Vault with Vault Tokens allows users to transfer their stake in the Vault as long as they don't have osGNO minted. It also allows Vault owners to develop a utility & liquidity ecosystem for GNO staked in their Vault.&#x20;

Meanwhile, tokenless Vaults protect users from triggering a tax event when depositing or withdrawing GNO from the Vault. A stake in the tokenless Vault cannot be transferred to another wallet.&#x20;

Presence of Vault Tokens is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault block rewards destination**

Allows Vaults to use either a Smoothing Pool or Own Escrow for collecting the block rewards.&#x20;

Using a Smoothing Pool helps achieve a stable Vault APY because block production rewards are shared among all the participating Vaults proportionately to their size. Using Own Escrow preserves the randomness of receiving block production duties and results in a more volatile Vault APY when the Vault has a small number of validators.&#x20;

Block rewards destination is defined by the Vault creator during Vault setup and cannot be changed later.

**Vault branding**

Allows Vault Admin to set the name, description and avatar for their Vault.&#x20;

Vault branding can be changed at any time.&#x20;

**Vault verification**

Vault verification provides certainty to Stakers that Vault branding is accurate, i.e. a Vault branded by Operator A is indeed controlled and run by Operator A. Verification is a manual process managed by the core StakeWise team.&#x20;
{% endtab %}
{% endtabs %}

#### StakeWise Operator Service

{% tabs %}
{% tab title="ETH" %}
The StakeWise Operator Service is designed to run seamlessly alongside any node setup, giving operators the freedom to run their preferred execution/consensus clients, MEV relay, distributed validator technology, etc. Operator Service is primarily responsible for the registration of validators.&#x20;

A full guide to setting up Operator Service can be found [here](../for-operators/operator-service/).

### Validator registration <a href="#user-content-validator-registration" id="user-content-validator-registration"></a>

Operator Service periodically checks whether a Vault has accumulated enough assets for registering new validator(s) and sends a registration transaction to the Vault. The validator registration process consists of the following steps:

1. Check whether Vault has accumulated enough assets to register a validator (e.g. 32 ETH for Ethereum)
2. Get the next free validator public key from the deposit data file attached to Operator Service. The validators are registered in the same order as specified in the deposit data file.
3. Obtain BLS signature for exit message using local keystores or remote signer.
4. Share the exit signature of the validator with StakeWise Oracles:
   1. Using [Shamir's secret sharing](https://en.wikipedia.org/wiki/Shamir's_secret_sharing), split validator's BLS signature. The number of shares is equal to the number of Oracles.
   2. Encrypt exit signatures with Oracles' public keys.
   3. Send encrypted exit signatures to all the Oracles and receive registration signatures from them.
5. Send transaction to Vault contract to register the validator.

Note, exit signatures can become invalid if the Oracle Network changes. For example, if an Oracle's private key gets compromised, the DAO will have to propose an update to the Oracle Network, triggering a rotation of all exit signatures across the protocol.

Operator Service periodically checks active validators of the Vault and if some exit signatures become outdated, Operator Service will submit a signature update transaction to the Vault.
{% endtab %}

{% tab title="GNO" %}
The StakeWise Operator Service is designed to run seamlessly alongside any node setup, giving operators the freedom to run their preferred execution/consensus clients, MEV relay, distributed validator technology, etc. Operator Service is primarily responsible for the registration of validators.&#x20;

A full guide to setting up Operator Service can be found [here](../for-operators/operator-service/).

### Validator registration <a href="#user-content-validator-registration" id="user-content-validator-registration"></a>

Operator Service periodically checks whether a Vault has accumulated enough assets for registering new validator(s) and sends a registration transaction to the Vault. The validator registration process consists of the following steps:

1. Check whether Vault has accumulated enough assets to register a validator (e.g., 1 GNO for Gnosis Chain)
2. Get the next free validator public key from the deposit data file attached to Operator Service. The validators are registered in the same order as specified in the deposit data file.
3. Obtain BLS signature for exit message using local keystores or remote signer.
4. Share the exit signature of the validator with StakeWise Oracles:
   1. Using [Shamir's secret sharing](https://en.wikipedia.org/wiki/Shamir's_secret_sharing), split validator's BLS signature. The number of shares is equal to the number of Oracles.
   2. Encrypt exit signatures with with Oracles' public keys.
   3. Send encrypted exit signatures to all the Oracles and receive registration signatures from them.
5. Send transaction to Vault contract to register the validator.

Note, exit signatures can become invalid if the Oracle Network changes. For example, if an Oracle's private key gets compromised, the DAO will have to propose an update to the Oracle Network, triggering a rotation of all exit signatures across the protocol.

Operator Service periodically checks active validators of the Vault and if some exit signatures become outdated, Operator Service will submit a signature update transaction to the Vault.
{% endtab %}
{% endtabs %}

#### Governance and management

Every Vault is an independent staking pool and its smart contracts cannot be unilaterally changed or upgraded by the StakeWise DAO.&#x20;

The DAO may implement changes to the Vault contracts to improve their efficiency and safety, in which case a new version of Vault contracts would become available to users. However, Vaults can always choose not to upgrade to the new version. This helps Vault owners preserve control over the staking experience they offer.

Every Vault also has several key roles for the internal management of the staking process.&#x20;

**Vault Admin**

Deploys the Vaults and sets the core parameters like the type of Vault and fee. Vault Admins also control the Vault's branding.

Vault Admin can be a single wallet, a multisig, or a DAO. Out of security considerations, Vault Admin cannot be changed once the Vault has been deployed.&#x20;

Vault Admin cannot change the core parameters of the Vault once it has been deployed. However, an Admin can assign the Access Manager and Keys Manager roles to other wallets, and change the recipient of the staking fee.&#x20;

**Access Manager**

Wallet with the power to add and remove wallets from the whitelist of a Private Vault.

By default, Vault Admin is also the Access Manager. However, an Admin can assign the Access Manager role to another wallet, and reclaim this role at any moment in the future.

**Keys Manager**

Wallet with the power to add new deposit data to a given Vault.&#x20;

By default, Vault Admin is also the Keys Manager. However, an Admin can assign the Keys Manager role to another wallet, and reclaim this role at any moment in the future.

Note that StakeWise always checks the validity of deposit data submitted to the Vault to ensure it contains the correct withdrawal address and hasn't been used before.

#### Operating a Vault

{% tabs %}
{% tab title="ETH" %}
**Vault operator(s)**

Entities or individuals who run validators for a Vault are known as Vault operator(s).

Vault Admin determines who the Vault operators are by uploading a deposit data file to the Vault. This file contains the public keys to the validators and the order in which they will be created when the Vault accumulates enough ETH. These keys are generated by Vault operators using StakeWise Operator Service, or another keygen software.

It is not possible to change an operator who is already running validators for a Vault without asking them to voluntarily exit their validators. However, it is possible to assign new operators for the validators that will be launched in the future by uploading new deposit data.

Vault Admin can assign the role of Keys Manager to another wallet to outsource the uploading of new deposit data (and hence the determination of Vault operators) to a third party.

**Vault state**

Every Vault has an internal accounting ledger, saved in the form of a Vault state, that keeps track of the value of stakers' participation in the Vault.

Any event that impacts the value of users' stake in the Vault (e.g. new ETH deposit into a Vault, ETH rewards being earned, MEV claimed from a Smoothing Pool etc.) or requires the latest value of users' stake in the Vault (e.g. minting or burning osETH) will require an update to the Vault state to ensure all values are up to date.

Any user-driven interaction with the Vault will trigger an update in the Vault state. In the absence of user-driven actions, Vault operator(s) can manually trigger the update whenever they see fit (optional).&#x20;
{% endtab %}

{% tab title="GNO" %}
**Vault operator(s)**

Entities or individuals who run validators for a Vault are known as Vault operator(s).

Vault Admin determines who the Vault operators are by uploading a deposit data file to the Vault. This file contains the public keys to the validators and the order in which they will be created when the Vault accumulates enough GNO. These keys are generated by Vault operators using StakeWise Operator Service, or another keygen software.

It is not possible to change an operator who is already running validators for a Vault without asking them to voluntarily exit their validators. However, it is possible to assign new operators for the validators that will be launched in the future by uploading new deposit data.

Vault Admin can assign the role of Keys Manager to another wallet to outsource the uploading of new deposit data (and hence the determination of Vault operators) to a third party.

**Vault state**

Every Vault has an internal accounting ledger, saved in the form of a Vault state, that keeps track of the value of stakers' participation in the Vault.

Any event that impacts the value of users' stake in the Vault (e.g. new GNO deposit into a Vault, GNO rewards being earned, MEV claimed from a Smoothing Pool etc.) or requires the latest value of users' stake in the Vault (e.g. minting or burning osGNO) will require an update to the Vault state to ensure all values are up to date.

Any user-driven interaction with the Vault will trigger an update in the Vault state. In the absence of user-driven actions, Vault operator(s) can manually trigger the update whenever they see fit (optional).&#x20;
{% endtab %}
{% endtabs %}

#### Whitelist

{% tabs %}
{% tab title="ETH" %}
Whitelist is a function in Private Vaults that allows Vault Admin to control who can deposit and withdraw ETH from the Vault.&#x20;

Once a Private Vault is deployed, Vault Admin can add or remove wallets from the whitelist to manage access to the Vault. Wallets added to the whitelist can stake ETH into the Vault. If a wallet is removed from the whitelist after making a deposit, it will still be able to unstake ETH from that Vault.

Vault Admin can also assign the role of Access Manager to another wallet to outsource the management of the whitelist to a third party.
{% endtab %}

{% tab title="GNO" %}
Whitelist is a function in Private Vaults that allows Vault Admin to control who can deposit and withdraw GNO from the Vault.&#x20;

Once a Private Vault is deployed, Vault Admin can add or remove wallets from the whitelist to manage access to the Vault. Wallets added to the whitelist can stake GNO into the Vault. If a wallet is removed from the whitelist after making a deposit, it will still be able to unstake GNO from that Vault.

Vault Admin can also assign the role of Access Manager to another wallet to outsource the management of the whitelist to a third party.
{% endtab %}
{% endtabs %}

#### Handling of MEV

{% tabs %}
{% tab title="ETH" %}
**Smoothing Pool**&#x20;

Smoothing Pool collects block proposal rewards from all participating validators (Vaults) and periodically distributes rewards to the participants, proportionately to their size.

For example, a Vault with only a few validators can receive periodic small payouts from the Smoothing Pool, which come from the block proposal rewards contributed by other participating Vaults. In return, when the Vault does get the chance to earn a block proposal reward, it will flow to the Smoothing Pool as well, to be shared amongst all participating Vaults.

Therefore, the main advantage of using the Smoothing Pool is achieving a consistent level of rewards from block production, and a consistent Vault APY.&#x20;

Any Vault that opts into using the Smoothing Pool is required to operate one of the StakeWise DAO-approved MEV relays. This is necessary to ensure a consistently high contribution to the Smoothing Pool from every participating Vault.

**MEV theft protection**

Smoothing Pool system relies on fair contributions from all participants. A Vault that uses the Smoothing Pool to collect block proposal rewards must not engage in any form of MEV theft that lowers its contribution to the Pool.&#x20;

To encourage fair behaviour, StakeWise delays the actual pay-out of ETH rewards from the Smoothing Pool to the Vault until the moment that the Vault contributes the expected amount of rewards for proposing a block.&#x20;

The expected amount is defined as the lowest possible reward that the proposing validator could have received for a block it proposed using one of the StakeWise DAO-approved relays.&#x20;

If the contribution is on par with or exceeds expectations, the rewards accumulated for the Vault in the Smoothing Pool to date are paid out.&#x20;

If the contribution is below the expected amount, the rewards that the Vault expected to receive from the Smoothing Pool are withheld in favour of other Pool participants. The Vault also receives an "MEV thief" status internally.&#x20;

**Own Escrow**

Own Escrow allows a Vault to choose an independent approach to earning block production rewards, like using any relay of choice, because it does not rely on sharing such rewards with other Vaults.

Using Own Escrow to collect block proposal rewards allows Vaults to build their own blocks or use any relay they see fit.&#x20;

Vaults that use Own Escrow and have only a few validators can expect a more volatile Vault APY because of the randomness associated with receiving block production duties.
{% endtab %}

{% tab title="GNO" %}
**Smoothing Pool**&#x20;

Smoothing Pool collects block proposal rewards from all participating validators (Vaults) and periodically distributes rewards to the participants, proportionately to their size.

For example, a Vault with only a few validators can receive periodic small payouts from the Smoothing Pool, which come from the block proposal rewards contributed by other participating Vaults. In return, when the Vault does get the chance to earn a block proposal reward, it will flow to the Smoothing Pool as well, to be shared amongst all participating Vaults.

Therefore, the main advantage of using the Smoothing Pool is achieving a consistent level of rewards from block production, and a consistent Vault APY.&#x20;

Any Vault that opts into using the Smoothing Pool is required to operate one of the StakeWise DAO-approved MEV relays. This is necessary to ensure a consistently high contribution to the Smoothing Pool from every participating Vault.

**MEV theft protection**

Smoothing Pool system relies on fair contributions from all participants. A Vault that uses the Smoothing Pool to collect block proposal rewards must not engage in any form of MEV theft that lowers its contribution to the Pool.&#x20;

To encourage fair behaviour, StakeWise delays the actual pay-out of GNO rewards (converted from xDAI) from the Smoothing Pool to the Vault until the moment that the Vault contributes the expected amount of rewards for proposing a block.&#x20;

The expected amount is defined as the lowest possible reward that the proposing validator could have received for a block it proposed using one of the StakeWise DAO-approved relays.&#x20;

If the contribution is on par with or exceeds expectations, the rewards accumulated for the Vault in the Smoothing Pool to date are paid out.&#x20;

If the contribution is below the expected amount, the rewards that the Vault expected to receive from the Smoothing Pool are withheld in favour of other Pool participants. The Vault also receives an "MEV thief" status internally.&#x20;

**Own Escrow**

Own Escrow allows a Vault to choose an independent approach to earning block production rewards, like using any relay of choice, because it does not rely on sharing such rewards with other Vaults.

Using Own Escrow to collect block proposal rewards allows Vaults to build their own blocks or use any relay they see fit.&#x20;

Vaults that use Own Escrow and have only a few validators can expect a more volatile Vault APY because of the randomness associated with receiving block production duties.
{% endtab %}
{% endtabs %}
