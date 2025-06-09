---
description: Learn about osETH and osGNO tokens in StakeWise V3
cover: ../.gitbook/assets/Frame 27513376 (1).png
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# osToken

Liquid staking in StakeWise V3 is powered by osTokens -  staked tokens that accrue staking rewards when held.&#x20;

{% tabs %}
{% tab title="osETH" %}
osETH represents ETH staked in Vaults and earns ETH rewards that accrue from their validators. osETH can always be redeemed for ETH from Vaults, helping it maintain an accurate price on DEXs.

A unique feature of osETH is that it can be minted against any Ethereum node, making access to liquid staking as permissionless and non-custodial as possible. This enables users to stake ETH however they like, including solo, and be able to farm, borrow and restake staked ETH in DeFi.

Permissionless minting of osETH allows it to be backed by a wide network of pools, solo stakers, DAOs, and other organizations staking ETH in unique ways that do not lead to the centralization of Ethereum.
{% endtab %}

{% tab title="osGNO" %}
osGNO represents GNO staked in Vaults and earns GNO rewards that accrue from their validators. osGNO can always be redeemed for GNO from Vaults, helping it maintain an accurate price on DEXs.

A unique feature of osGNO is that it can be minted against any Gnosis Chain node, making access to liquid staking as permissionless and non-custodial as possible. This enables users to stake GNO however they like, including solo, and be able to farm with staked GNO in DeFi.

Permissionless minting of osGNO allows it to be backed by a wide network of pools, solo stakers, DAOs, and other organizations staking GNO in unique ways that do not lead to the centralization of Gnosis Chain.
{% endtab %}
{% endtabs %}

### Main characteristics

#### Exchange rate

{% tabs %}
{% tab title="osETH" %}
osETH is an ERC-20 token that accrues ETH staking rewards when held. It captures the staking rewards being earned by the staked ETH that is backing the token.&#x20;

Mechanically, the accrual of rewards by validators is reflected in the constant increase in the amount of ETH that osETH can be redeemed for, known as the **fair osETH exchange rate**. The increase in redemption value to reflect the accrual of rewards makes osETH a repricing token.

At osETH launch, the exchange rate starts at 1.00 ETH per osETH and increases as more staking rewards are earned. The rate of increase is reflected in the osETH APY, which is always quoted net of the StakeWise DAO fees.&#x20;

_Example_: if the staked ETH that backs osETH earned 5% APY over the past year (after Vault fees), the osETH exchange rate would increase from 1 ETH per osETH to 1.0475 ETH per osETH.

Note that the osETH growth rate follows the APY of the lowest-yielding 99.99% LTV Vault.
{% endtab %}

{% tab title="osGNO" %}
osGNO is an ERC-20 token that accrues GNO staking rewards when held. It captures the staking rewards being earned by the staked GNO that is backing the token.&#x20;

Mechanically, the accrual of rewards by validators is reflected in the constant increase in the amount of GNO that osGNO can be redeemed for, known as the **fair osGNO exchange rate**. The increase in redemption value to reflect the accrual of rewards makes osGNO a repricing token.

At osGNO launch, the exchange rate starts at 1.00 GNO per osGNO and increases as more staking rewards are earned. The rate of increase is reflected in the osGNO APY, which is always quoted net of the StakeWise DAO fees.&#x20;

_Example_: if the staked GNO that backs osGNO earned 5% APY over the past year (after Vault fees), the osGNO exchange rate would increase from 1 GNO per osGNO to 1.0475 GNO per osGNO.

Note that the osGNO growth rate follows the APY of the lowest-yielding 99.95% LTV Vault.
{% endtab %}
{% endtabs %}

#### In-built slashing protection

{% tabs %}
{% tab title="osETH" %}
osETH can be minted against any Ethereum node, including those that perform poorly.&#x20;

**90% LTV Vaults**

To protect 90% LTV Vault osETH holders against the risk of poor performance, slashing, and general failure of permissionless nodes, osETH has an **excess backing** of staked ETH that is used to cover for the shortfall in performance and absorb slashing losses. This gives 90% LTV Vaults osETH an in-built slashing protection feature.&#x20;

**99.99% LTV Vaults**

99.99% Vault operators are required to place a 5M SWISE bond before such capability is provided by the StakeWise DAO. This ensures that other osETH holders remain unaffected by Vault-specific penalties or slashing risks.&#x20;

Also, in a 99.99% LTV Vault, your position is always considered healthy because osETH APY matches the APY of the lowest-yielding 99.99% LTV Vault. This ensures that your Vault's APY is never lower than osETH's APY.&#x20;

Stakers in Vaults benefit from these slashing protection mechanisms because when they mint osETH, they are not affected by the performance or slashing of any nodes except the nodes that run validators for their Vault.

**Buying osETH on DEXs**

Stakers who buy osETH on DEXs don't have exposure to any particular Vault and hence are fully insulated against any slashing losses and poor performance that may occur.&#x20;

[<mark style="color:blue;">Read more about the excess backing of osETH -></mark>](ostoken.md#backing)
{% endtab %}

{% tab title="osGNO" %}
osGNO can be minted against any Gnosis node, including those that perform poorly.&#x20;

**90% LTV Vaults**

To protect 90% LTV Vault osGNO holders against the risk of poor performance, slashing, and general failure of permissionless nodes, osGNO has an **excess backing** of staked GNO that is used to cover for the shortfall in performance and absorb slashing losses. This gives 90% LTV Vault osGNO an in-built slashing protection feature.&#x20;

**99.95% LTV Vaults**

99.95% Vault operators are required to place a 1M SWISE bond before such capability is provided by the StakeWise DAO. This ensures that other osGNO holders remain unaffected by Vault-specific penalties or slashing risks.&#x20;

Also, in a 99.95% LTV Vault, your position is always considered healthy because osGNO APY matches the APY of the lowest-yielding 99.95% LTV Vault. This ensures that your Vault's APY is never lower than osGNO's APY.&#x20;

Stakers in Vaults benefit from these slashing protection mechanisms because when they mint osGNO, they are not affected by the performance or slashing of any nodes except the nodes that run validators for their Vault.

**Buying osGNO on DEXs**

Stakers who buy osGNO on DEXs don't have exposure to any particular Vault and hence are fully insulated against any slashing losses and poor performance that may occur.&#x20;

[<mark style="color:blue;">Read more about the excess backing of osGNO -></mark>](ostoken.md#backing)
{% endtab %}
{% endtabs %}

#### Redeemable for ETH or GNO

{% tabs %}
{% tab title="osETH" %}
osETH is backed by staked ETH in Vaults, and is redeemable for ETH in their validators.

Redemption of osETH for ETH always happens at the underlying exchange rate between the two tokens. The exchange rate is determined by StakeWise Oracles based on the performance of Vaults.

Redemption of osETH for ETH is instant if there is enough unbonded ETH in the protocol. If the amount of unbonded ETH is not enough to meet the volume of redemption requests, the protocol will exit validators to withdraw a sufficient amount of ETH for full redemption.&#x20;

[<mark style="color:blue;">Read more about the osETH redemption mechanism -></mark>](ostoken.md#redemption-mechanism)
{% endtab %}

{% tab title="osGNO" %}
osGNO is backed by staked GNO in Vaults, and is redeemable for GNO in their validators.

Redemption of osGNO for GNO always happens at the underlying exchange rate between the two tokens. The exchange rate is determined by StakeWise Oracles based on the performance of Vaults.

Redemption of osGNO for GNO is instant if there is enough unbonded GNO in the protocol. If the amount of unbonded GNO is not enough to meet the volume of redemption requests, the protocol will exit validators to withdraw a sufficient amount of GNO for full redemption.&#x20;

[<mark style="color:blue;">Read more about the osGNO redemption mechanism -></mark>](ostoken.md#redemption-mechanism)
{% endtab %}
{% endtabs %}

#### osToken APY

{% tabs %}
{% tab title="osETH" %}
<pre class="language-markup" data-overflow="wrap"><code class="lang-markup"><strong>osETH APY = APY of the lowest-yielding 99.99% LTV Vault
</strong></code></pre>

Find the Net Vault APY formula [here](https://docs.stakewise.io/protocol-overview-in-depth/vaults#vault-apy-formula).
{% endtab %}

{% tab title="osGNO" %}
<pre><code><strong>osGNO APY = APY of the lowest-yielding 99.95% LTV Vault
</strong></code></pre>

Find the Net Vault APY formula [here](https://docs.stakewise.io/protocol-overview-in-depth/vaults#vault-apy-formula).
{% endtab %}
{% endtabs %}

#### Staking fee

{% tabs %}
{% tab title="osETH" %}
StakeWise DAO charges a 5% fee on the rewards accumulated by osETH, and continuously applies the fee to the balance of osETH a user has minted from the Vault. The fee is charged in osETH, meaning that the amount of osETH a user must return to the Vault constantly increases proportionately to the fee.

_Example_: a user's minted osETH has accumulated 1 ETH in rewards on their stake. StakeWise will apply a 0.05 ETH fee to the user's osETH balance using the current osETH exchange rate. If the rate is 1.05 ETH/osETH, the user's total balance of minted osETH will increase by 0.05/1.05 = 0.04761904761 osETH.&#x20;
{% endtab %}

{% tab title="osGNO" %}
StakeWise DAO charges a 5% fee on the rewards accumulated by osGNO, and continuously applies the fee to the balance of osGNO a user has minted from the Vault. The fee is charged in osGNO, meaning that the amount of osGNO a user must return to the Vault constantly increases proportionately to the fee.

_Example_: a user's minted osGNO has accumulated 1 GNO in rewards on their stake. StakeWise will apply a 0.05 GNO fee to the user's osGNO balance using the current osGNO exchange rate. If the rate is 1.05 GNO/osGNO, the user's total balance of minted osGNO will increase by 0.05/1.05 = 0.04761904761 osGNO.
{% endtab %}
{% endtabs %}

### Minting and burning

#### Minting

{% tabs %}
{% tab title="osETH" %}
osETH is a liquid staking token that represents ETH staked in Vaults. It can be minted by any staker in Vaults to make their stake liquid.

Like every liquid staking token, osETH requires backing by actual staked ETH in validators.  Whenever users mint osETH for their stake in Vaults, new osETH is created with users' staked ETH as backing (i.e. collateral). This ensures that someone purchasing osETH on an exchange can redeem it for the underlying ETH at any time, giving the token value in DeFi.

The amount of osETH a user can mint depends on the value of their ETH stake in the Vault, osETH exchange rate, and the excess backing limit imposed by the StakeWise DAO (applicable to 90% LTV Vaults).&#x20;

**90% LTV Vaults**

The formula is as follows:&#x20;

```
Max amount of osETH to be minted = amount of ETH staked * 90%
```

At any time, the value of osETH that can be minted by a staker will not exceed 90% of the value of their ETH stake in the Vault. This limit for 90% LTV Vault is defined by the **minting threshold**, which is a parameter set by the DAO.&#x20;

_Example_: a user staked 100 ETH in the Vault. At 1.05 ETH per osETH exchange rate and the 90% minting threshold, the maximum amount of osETH a staker can mint is 100 \* 90% / 1.05 = 85.71429 osETH. The maximum value of osETH minted in this case is 100 ETH \* 90% = 90 ETH, which fits the minting threshold requirement.&#x20;

**99.99% LTV Vaults**

The formula is as follows:&#x20;

```
Max amount of osETH to be minted = amount of ETH staked * 99.99%
```

At any time, the value of osETH that can be minted by a staker will not exceed 99.99% of the value of their ETH stake in the Vault. This limit for 99.99% LTV Vault is defined by the **minting threshold**, which is a parameter set by the DAO.&#x20;

_Example_: a user staked 100 ETH in the Vault. At 1.05 ETH per osETH exchange rate and the 99.99% minting threshold, the maximum amount of osETH a staker can mint is 100 \* 99.99% / 1.05 = 95.22857 osETH. The maximum value of osETH minted in this case is 100 ETH \* 99.99% = 99.99 ETH, which fits the minting threshold requirement.&#x20;

[<mark style="color:blue;">Read our guide about minting osETH from a Vault -></mark>](https://docs.stakewise.io/guides/ostoken#minting-ostoken-from-vaults-to-start-liquid-staking)
{% endtab %}

{% tab title="osGNO" %}
osGNO is a liquid staking token that represents GNO staked in Vaults. It can be minted by any staker in Vaults to make their stake liquid.

Like every liquid staking token, osGNO requires backing by actual staked GNO in validators.  Whenever users mint osGNO for their stake in Vaults, new osGNO is created with users' staked GNO as backing (i.e. collateral). This ensures that someone purchasing osGNO on an exchange can redeem it for the underlying GNO at any time, giving the token value in DeFi.

The amount of osGNO a user can mint depends on the value of their GNO stake in the Vault, osGNO exchange rate, and the excess backing limit imposed by the StakeWise DAO (applicable to 90% LTV Vaults).&#x20;

**90% LTV Vaults**

The formula is as follows:&#x20;

```
Max amount of osGNO to be minted = amount of GNO staked * 90%
```

At any time, the value of osGNO that can be minted by a staker will not exceed 90% of the value of their GNO stake in the Vault. This limit for 90% LTV Vault is defined by the **minting threshold**, which is a parameter set by the DAO.&#x20;

_Example_: a user staked 100 GNO in the Vault. At 1.05 GNO per osGNO exchange rate and the 90% minting threshold, the maximum amount of osGNO a staker can mint is 100 \* 90% / 1.05 = 85.71429 osGNO. The maximum value of osGNO minted in this case is 100 GNO \* 90% = 90 GNO, which fits the minting threshold requirement.&#x20;

**99.95% LTV Vaults**

The formula is as follows:&#x20;

```
Max amount of osGNO to be minted = amount of GNO staked * 99.95%
```

At any time, the value of osGNO that can be minted by a staker will not exceed 99.95% of the value of their GNO stake in the Vault. This limit for 99.95% LTV Vault is defined by the **minting threshold**, which is a parameter set by the DAO.&#x20;

_Example_: a user staked 100 GNO in the Vault. At 1.05 GNO per osGNO exchange rate and the 99.95% minting threshold, the maximum amount of osGNO a staker can mint is 100 \* 99.95% / 1.05 = 95.19048 osGNO. The maximum value of osGNO minted in this case is 100 GNO \* 99.95% = 99.95 GNO, which fits the minting threshold requirement. &#x20;

[<mark style="color:blue;">Read our guide about minting osGNO from a Vault -></mark>](https://docs.stakewise.io/guides/ostoken#minting-ostoken-from-vaults-to-start-liquid-staking)
{% endtab %}
{% endtabs %}

#### Backing

{% tabs %}
{% tab title="osETH" %}
osETH minting always requires excess backing: overcollateralization in 90% LTV Vaults or a SWISE bond in 99.99% LTV Vaults. This protects osETH holders from bad performance and slashing risks associated with permissionless access to the token.&#x20;

**90% LTV Vaults**

Overcollateralization means that stakers in 90% LTV Vaults can mint osETH for up to 90% of the value of their ETH stake, using their stake in the Vault as backing for the osETH token. Stakers continue to accumulate ETH rewards on 100% of their staked ETH, but only up to 90% of their total stake can be made liquid.

_Example_: staking 100 ETH into a Vault, a user can mint up to 90 ETH worth of their stake in osETH (according to the minting threshold of 90%). If the exchange rate is 1.05 ETH per osETH, then the user can mint a maximum of 90/1.05 = 85.71428 osETH tokens worth 90 ETH. This is the amount of stake they will have in liquid form.

**99.99% LTV Vaults**

Stakers in 99.99% LTV Vaults can mint osETH for up to 99.99% of the value of their ETH stake, using their stake in the Vault as backing for the osETH token. Stakers continue to accumulate ETH rewards on 100% of their staked ETH, but only up to 99.99% of their total stake can be made liquid.

_Example_: staking 100 ETH into a Vault, a user can mint up to 99.99 ETH worth of their stake in osETH (according to the minting threshold of 99.99%). If the exchange rate is 1.05 ETH per osETH, then the user can mint a maximum of 99.99/1.05 = 95.22857 osETH tokens worth 99.99 ETH. This is the amount of stake they will have in liquid form.

**Buying osETH on DEXs**

Note that users who purchase osETH on an exchange and redeem the token for the underlying ETH will not claim the excess backing provided by stakers in Vaults. Instead, it belongs to the stakers who originally minted osETH.

**How excess backing is used in 90% LTV Vaults**

The excess backing provided to osETH is used as a buffer against poor performance and potential slashing-related losses. It ensures that if the validators of a Vault get slashed or accrue penalties, the loss of ETH staked in that Vault does not cause osETH to become unbacked. Instead, any such losses are absorbed by the excess backing.&#x20;

_Example:_ a Vault is staking 1,000 ETH and minted 900 osETH at the exchange rate 1.00 ETH per osETH. Suppose the Vault got slashed and will lose \~34 ETH in slashing-related penalties. Because the Vault has 100 ETH of excess backing, the 34 ETH loss will be absorbed by this buffer, without impacting other osETH holders. Instead, the loss will be borne only by the stakers in the slashed Vault.

**How excess backing is used in 99.99% LTV Vaults**

The backing comes in the form of a 5m SWISE bond that the Vault operator must lock in a DAO-controlled address before receiving 99.99% LTV capability.

The 5m SWISE bond ensures that if the validators of a Vault get slashed or accrue penalties, the loss of ETH staked in that Vault does not cause osETH to become unbacked. Instead, any such losses are absorbed by the 5m SWISE bond placed when the 99.99% osETH minting capability was approved for the Vault by the DAO.&#x20;

_Example:_ a Vault is staking 1,000 ETH and minted 999.9 osETH at the exchange rate 1.00 ETH per osETH. Suppose the Vault got slashed and will lose \~34 ETH in slashing-related penalties. Because the Vault has 5m SWISE of backing, the 34 ETH loss will be absorbed by this 5m SWISE buffer, without impacting other osETH holders. Instead, the loss will be borne only by the stakers in the slashed Vault.
{% endtab %}

{% tab title="osGNO" %}
osGNO minting always requires excess backing: overcollateralization in 90% LTV Vaults or a SWISE bond in 99.95% LTV Vaults. This protects osGNO holders from bad performance and slashing risks associated with permissionless access to the token.

**90% LTV Vaults**

Overcollateralization means that stakers in 90% LTV Vaults can mint osGNO for up to 90% of the value of their GNO stake, using their stake in the Vault as backing for the osGNO token. Stakers continue to accumulate GNO rewards on 100% of their staked GNO, but only up to 90% of their total stake can be made liquid.

Example: staking 100 GNO into a Vault, a user can mint up to 90 GNO worth of their stake in osGNO (according to the minting threshold of 90%). If the exchange rate is 1.05 GNO per osGNO, then the user can mint a maximum of 90/1.05 = 85.71428 osGNO tokens worth 90 GNO. This is the amount of stake they will have in liquid form.

**99.95% LTV Vaults**

Stakers in 99.95% LTV Vaults can mint osGNO for up to 99.95% of the value of their GNO stake, using their stake in the Vault as backing for the osGNO token. Stakers continue to accumulate GNO rewards on 100% of their staked GNO, but only up to 99.95% of their total stake can be made liquid.

_Example:_ staking 100 GNO into a Vault, a user can mint up to 99.95 GNO worth of their stake in osGNO (according to the minting threshold of 99.95%). If the exchange rate is 1.05 GNO per osGNO, then the user can mint a maximum of 99.95/1.05 = 95.19048 osGNO tokens worth 99.95 GNO. This is the amount of stake they will have in liquid form.

**Buying osGNO on DEXs**

Note that users who purchase osGNO on an exchange and redeem the token for the underlying GNO will not claim the excess backing provided by stakers in Vaults. Instead, it belongs to the stakers who originally minted osGNO.

**How excess backing is used in 90% LTV Vaults**

The excess backing provided to osGNO is used as a buffer against poor performance and potential slashing-related losses. It ensures that if the validators of a Vault get slashed or accrue penalties, the loss of GNO staked in that Vault does not cause osGNO to become unbacked. Instead, any such losses are absorbed by the excess backing.

Example: a Vault is staking 1,000 GNO and minted 900 osGNO at the exchange rate 1.00 GNO per osGNO. Suppose the Vault got slashed and will lose \~34 GNO in slashing-related penalties. Because the Vault has 100 GNO of excess backing, the 34 GNO loss will be absorbed by this buffer, without impacting other osGNO holders. Instead, the loss will be borne only by the stakers in the slashed Vault.

**How backing is used in 99.95% LTV Vaults**

The backing comes in the form of a 1m SWISE bond that the Vault operator must lock in a DAO-controlled address before receiving 99.95% LTV capability.

The 1m SWISE bond ensures that if the validators of a Vault get slashed or accrue penalties, the loss of GNO staked in that Vault does not cause osGNO to become unbacked. Instead, any such losses are absorbed by the 1m SWISE bond placed when the 99.95% osGNO minting capability was approved for the Vault by the DAO.

_Example:_ a Vault is staking 1,000 GNO and minted 999.5 osGNO at the exchange rate 1.00 GNO per osGNO. Suppose the Vault got slashed and will lose \~34 GNO in slashing-related penalties. Because the Vault has 1m SWISE of backing, the 34 GNO loss will be absorbed by this buffer, without impacting other osGNO holders. Instead, the loss will be borne only by the stakers in the slashed Vault.
{% endtab %}
{% endtabs %}

#### Position health

{% tabs %}
{% tab title="osETH" %}
StakeWise continuously monitors the value of minted osETH tokens relative to the value of staked ETH backing them to ensure a healthy LTV level.

The most effective way to maintain a healthy LTV level for osETH is to not allow individual stakers' osETH positions to grow larger than a certain percentage of their ETH stake in the Vault (applicable to 90% LTV Vaults). If this happens, StakeWise must enable someone to forcibly burn the osETH that these stakers minted, removing poorly backed osETH tokens from the supply.&#x20;

StakeWise uses a parameter known as **position health** to track the value of osETH minted by stakers relative to the value of their ETH stake in the Vault.

Here is how position health can change in response to changes in values of osETH minted and staked ETH value:

**90% LTV Vaults**&#x20;

* **Healthy:** value of minted osETH does not exceed 90% of the staked ETH value a staker has in the Vault.
* **Moderate:** value of minted osETH exceeds 90% of the staked ETH value a staker has in the Vault but remains below 91%.
* **Risky:** value of minted osETH exceeds 91% of the staked ETH value a staker has in the Vault but remains below 92%.
* **Unhealthy:** value of minted osETH exceeds 92% of the staked ETH value a staker has in the Vault.

Some risky osETH positions will participate in the redemption mechanism for osETH, while unhealthy positions will be subject to forced burning known as liquidation.

**99.99% LTV Vaults**&#x20;

* In a 99.99% LTV Vault, your position is always considered healthy because osETH APY matches the APY of the lowest-yielding 99.99% LTV Vault. This means that your Vault's APY is never lower than osETH's APY. Thus, maintaining the stability of your position.

**What affects position health**

Position health depends on the value of minted osETH relative to the value of ETH staked. Anything that affects these values will also impact position health, either abruptly or over time.&#x20;

The most frequent reason for a change in position health is the discrepancy between the Vault APY and osETH APY\*. If the value of minted osETH grows much faster than the value of staked ETH position in the Vault, staker's position health will deteriorate.&#x20;

\*The impact of APY discrepancies on position health applies only to 90% LTV Vaults, as osETH APY is set to match the lowest-yielding 99.99% LTV Vault. If a 90% LTV Vault earns an APY lower than osETH APY, the position's health will deteriorate over time.

**90% LTV Vault APY may underperform osETH APY also due to:**&#x20;

* Charging higher fees than the market average
* Inconsistent attestation performance
* Large amount of unbonded ETH relative to Vault TVL
* Growth in TVL during long validator activation queue in the Beacon Chain, and&#x20;
* MEV theft

**99.99% LTV Vault APY cannot underperform osETH APY as its APY directly determines osETH APY.**&#x20;

Outperformance in both 90% and 99.99% LTV Vaults is related to charging lower than market fees, excellent attestation performance, and custom MEV strategies.&#x20;

A sudden deterioration in position health may signal a loss of ETH by the Vault due to slashing or MEV theft when using Smoothing Pool. In situations where a staker's position health in the Vault has suddenly deteriorated, StakeWise recommends burning any minted osETH and unstaking from the Vault.&#x20;

[<mark style="color:blue;">Read our guide about maintaining osETH position health -></mark>](https://docs.stakewise.io/guides/ostoken#maintaining-a-healthy-ostoken-position)
{% endtab %}

{% tab title="osGNO" %}
StakeWise continuously monitors the value of minted osGNO tokens relative to the value of staked GNO backing them to ensure a healthy LTV level.

The most effective way to maintain a healthy LTV level for osGNO is to not allow individual stakers' osGNO positions to grow larger than a certain percentage of their GNO stake in the Vault (applicable to 90% LTV Vaults). If this happens, StakeWise must enable someone to forcibly burn the osGNO that these stakers minted, removing poorly backed osGNO tokens from the supply.

StakeWise uses a parameter known as position health to track the value of osGNO minted by stakers relative to the value of their GNO stake in the Vault.

Here is how position health can change in response to changes in values of osGNO minted and staked GNO value:

**90% LTV** **Vaults**

* **Healthy**: value of minted osGNO does not exceed 90% of the staked GNO value a staker has in the Vault.
* **Moderate**: value of minted osGNO exceeds 90% of the staked GNO value a staker has in the Vault but remains below 91%.
* **Risky**: value of minted osGNO exceeds 91% of the staked GNO value a staker has in the Vault but remains below 92%.
* **Unhealthy**: value of minted osGNO exceeds 92% of the staked GNO value a staker has in the Vault.

**99.95% LTV Vaults**

* In a 99.95% LTV Vault, your position is always considered healthy because osGNO APY matches the APY of the lowest-yielding 99.95% LTV Vault. This ensures that your Vault's APY is never lower than osGNO's APY. Thus, maintaining the stability of your position.

Some risky osGNO positions will participate in the redemption mechanism for osGNO, while unhealthy positions will be subject to forced burning known as liquidation.

**What affects position health**

Position health depends on the value of minted osGNO relative to the value of GNO staked. Anything that affects these values will also impact position health, either abruptly or over time.

The most frequent reason for a change in position health is the discrepancy between the Vault APY and osGNO APY\*. If the value of minted osGNO grows much faster than the value of staked GNO position in the Vault, staker's position health will deteriorate.

\*The impact of APY discrepancies on position health applies only to 90% LTV Vaults, as osGNO APY is set to match the lowest-yielding 99.95% LTV Vault. If a 90% LTV Vault earns an APY lower than osGNO APY, the position's health will deteriorate over time.

**90% LTV Vault APY may underperform osGNO APY also due to:**

* Charging higher fees than the market average
* Inconsistent attestation performance
* Large amount of unbonded GNO relative to Vault TVL
* Growth in TVL during long validator activation queue in the Beacon Chain, and
* MEV theft

**99.95% LTV Vault APY cannot underperform osGNO APY as its APY directly determines osGNO APY.**

Outperformance in both 90% and 99.95% LTV Vaults is related to charging lower than market fees, excellent attestation performance, and custom MEV strategies.

A sudden deterioration in position health may signal a loss of GNO by the Vault due to slashing or MEV theft when using Smoothing Pool. In situations where a staker's position health in the Vault has suddenly deteriorated, StakeWise recommends burning any minted osGNO and unstaking from the Vault.

[<mark style="color:blue;">Read our guide about maintaining osGNO position health -></mark>](https://docs.stakewise.io/guides/ostoken#maintaining-a-healthy-ostoken-position)
{% endtab %}
{% endtabs %}

#### Burning

{% tabs %}
{% tab title="osETH" %}
Users' staked ETH in Vaults is used as backing when they mint osETH. osETH relies on this backing to maintain value on the secondary market. To prevent users from minting unbacked osETH, StakeWise locks users' staked ETH until the osETH they minted is fully returned to the Vault. The latter is known as osETH burning.

The amount of osETH to be burned will equal the sum of the original amount minted plus the StakeWise DAO commission, which is set to 5% of the rewards osETH accumulated.

[<mark style="color:blue;">Read more about the StakeWise DAO fee -></mark>](ostoken.md#staking-fee)

Note that burning the full outstanding amount of osETH is necessary to fully unstake from the Vault. If less osETH is burned, user's ETH stake will be withdrawable only partially in order to maintain appropriate position health.&#x20;

The amount of ETH that can be unstaked immediately will be based on position health, where the osETH position must remain healthy (i.e. up to 90% of staked ETH in 90% LTV Vaults and up to 99.99% in 99.99% LTV Vaults) after some ETH has been unstaked. This is calculated by the following formula:

**90% LTV Vaults:**

{% code overflow="wrap" %}
```
Amount of ETH that can be unstaked = amount of ETH staked - (amount of osETH minted * osETH exchange rate / 0.9)
```
{% endcode %}

**99.99% LTV Vaults:**

```
Amount of ETH that can be unstaked = amount of ETH staked - 
(amount of osETH minted * osETH exchange rate / 0.9999)
```

**90% LTV Vault Example**

A user has 100 ETH staked in a Vault and 50 osETH minted. At an exchange rate of 1.05 ETH/osETH, the value of minted osETH is 52.5 ETH, so the user's minted osETH value is 52.5/100 = 52.5% of the staked ETH value, making their position healthy.&#x20;

The user must maintain position health at a healthy level, so the maximum amount of ETH that can be unstaked is 100 - (52.5 / 0.9) = 41.667 ETH. To confirm, the value of minted osETH relative to the value of staked ETH after unstaking will be 52.5 / (100-41.667) = 0.9, i.e. the required 90%.&#x20;

**99.99% LTV Vault Example**

A user has 100 ETH staked in a Vault and 50 osETH minted. At an exchange rate of 1.05 ETH/osETH, the value of minted osETH is 52.5 ETH, so the user's minted osETH value is 52.5/100 = 52.5% of the staked ETH value, making their position healthy.&#x20;

The user must maintain position health at a healthy level, so the maximum amount of ETH that can be unstaked is 100 - (52.5 / 0.9999) = 47.49475 ETH. To confirm, the value of minted osETH relative to the value of staked ETH after unstaking will be 52.5 / (100-47.49475) = 0.9999, i.e. the required 99.99%.&#x20;

[<mark style="color:blue;">Read our guide about burning osETH in the Vault -></mark>](https://docs.stakewise.io/guides/ostoken#burning-ostoken-to-stop-liquid-staking)
{% endtab %}

{% tab title="osGNO" %}
Users' staked GNO in Vaults is used as backing when they mint osGNO. oGNO relies on this backing to maintain value on the secondary market. To prevent users from minting unbacked osGNO, StakeWise locks users' staked GNO until the osGNO they minted is fully returned to the Vault. The latter is known as osGNO burning.

The amount of osGNO to be burned will equal the sum of the original amount minted plus the StakeWise DAO commission, which is set to 5% of the rewards osGNO accumulated.

[<mark style="color:blue;">Read more about the StakeWise DAO fee -></mark>](ostoken.md#staking-fee)

Note that burning the full outstanding amount of osGNO is necessary to fully unstake from the Vault. If less osGNO is burned, user's GNO stake will be withdrawable only partially in order to maintain appropriate position health.&#x20;

The amount of GNO that can be unstaked immediately will be based on position health, where the osGNO position must remain healthy (i.e. up to 90% of staked GNO in 90% LTV Vaults and up to 99.95% in 99.95% LTV Vaults) after some GNO has been unstaked. This is calculated by the following formula:

**90% LTV Vaults:**

{% code overflow="wrap" %}
```
Amount of GNO that can be unstaked = amount of GNO staked - (amount of osGNO minted * osGNO exchange rate / 0.9)
```
{% endcode %}

**99.95% LTV Vaults:**

```
Amount of GNO that can be unstaked = amount of GNO staked - 
(amount of osGNO minted * osGNO exchange rate / 0.9995)
```

**90% LTV Vault Example**

A user has 100 GNO staked in a Vault and 50 osGNO minted. At an exchange rate of 1.05 GNO/osGNO, the value of minted osGNO is 52.5 GNO, so the user's minted osGNO value is 52.5/100 = 52.5% of the staked GNO value, making their position healthy.&#x20;

The user must maintain position health at a healthy level, so the maximum amount of GNO that can be unstaked is 100 - (52.5 / 0.9) = 41.667 GNO. To confirm, the value of minted osGNO relative to the value of staked GNO after unstaking will be 52.5 / (100-41.667) = 0.9, i.e. the required 90%.&#x20;

**99.95% LTV Vault Example**

A user has 100 GNO staked in a Vault and 50 osGNO minted. At an exchange rate of 1.05 GNO/osGNO, the value of minted osGNO is 52.5 GNO, so the user's minted osGNO value is 52.5/100 = 52.5% of the staked GNO value, making their position healthy.&#x20;

The user must maintain position health at a healthy level, so the maximum amount of GNO that can be unstaked is 100 - (52.5 / 0.9995) = 47.47374 GNO. To confirm, the value of minted osGNO relative to the value of staked GNO after unstaking will be 52.5 / (100-47.47374) = 0.9995, i.e. the required 99.95%.&#x20;

[<mark style="color:blue;">Read our guide about burning osGNO in the Vault -></mark>](https://docs.stakewise.io/guides/ostoken#burning-ostoken-to-stop-liquid-staking)
{% endtab %}
{% endtabs %}

### Peg stability

#### Redemption mechanism

{% tabs %}
{% tab title="osETH" %}
StakeWise makes its best efforts to ensure that the value of osETH on the exchanges corresponds to its fair exchange rate. The ability to receive ETH in exchange for osETH at the fair exchange rate is the key mechanism to ensure price stability, and relies on the redemption mechanism.

The osETH redemption mechanism allows anyone to redeem osETH natively via StakeWise for its underlying value (staked ETH backing the osETH tokens). Redemption happens when users burn osETH they acquired on the exchanges and withdraw ETH backing from Vaults at the fair osETH exchange rate.

The process of redeeming osETH reduces the osETH positions of certain stakers in Vaults, allowing them to improve their position health without manual actions. If the value of a user's osETH position in the 90% LTV Vault reaches 91.5% of their staked ETH value, anyone can step in and burn a certain amount of osETH from their position in exchange for redeeming a fair amount of ETH backing from the Vault.&#x20;

The amount is determined by the osETH exchange rate and the amount of osETH burned using the following formula:

**90% LTV Vaults**

{% code overflow="wrap" %}
```
Amount of osETH to be redeemed = 10 * amount of osETH currently minted - 9 * amount of ETH staked / osETH exchange rate
```
{% endcode %}

The 91.5% level for initiating redemptions is known as the **redemption threshold** and is set by the StakeWise DAO.

Note that users always have the ability to improve their position health to avoid redemption.

**99.99% Vaults**

In a 99.99% LTV Vault, your position is always considered healthy because osETH APY matches the APY of the lowest-yielding 99.99% LTV Vault. This ensures that your Vault's APY is never lower than osETH's APY. Thus, maintaining the stability of your position.

[<mark style="color:blue;">Read our guide about maintaining a healthy osETH position -></mark>](https://docs.stakewise.io/guides/ostoken#maintaining-a-healthy-ostoken-position)

There is a limit to how much osETH can be burned from any given osETH position. This amount is defined by the amount of osETH that must be redeemed in order to bring a user's osETH position health back to a healthy level (90%). Redemptions also don't incur any fees, have no economic impact on the users in Vaults, and don't expose those who redeem osETH to adverse Vault performance or slashing.

**90% LTV Vault Example**

User has minted 87.238 osETH that is now worth 91.6 ETH against a staked ETH position that is currently worth 100 ETH. The user's position is open to redemption because the value of minted osETH relative to their ETH stake exceeds the redemption threshold, i.e. 91.5%.&#x20;

Users who bought osETH on exchanges will use a portion of the position to redeem their osETH, with the amount based on the osETH exchange rate. If the osETH exchange rate is currently 1.05 ETH/osETH, users would be able to redeem 10 \* 87.238 - 9 \* 100 / 1.05 = 15.238 osETH for 16 ETH, bringing the position back down to 90% of the staked ETH value.&#x20;

**Impact on users in 90% LTV Vaults**

osETH redemptions do not lead to stakers in Vaults losing their capital. When someone burns a portion of a staker's minted osETH on their behalf, the staker gets to keep the proportional amount of osETH, without the need to burn it to fully unstake from the Vault. It is equivalent to simply buying that portion of osETH on the exchange.&#x20;

Meanwhile, the health of users' remaining osETH positions improves with redemptions.&#x20;

_Example_: a user starts off with 87.238095 osETH minted and 100 ETH staked in the Vault, which implies a 1.05 ETH/osETH exchange rate. Their osETH position is worth 91.6% of their staked ETH value, triggering a redemption. 15.238095 osETH is redeemed for 16 ETH, reducing the staker's outstanding minted osETH from 87.238095 to 72, and their stake in the Vault from 100 to 84. As a result, osETH position health improves to 90% of their staked ETH value. The user can claim 84 staked ETH from the Vault by burning 72 osETH, and gets to keep the 15.238095 osETH that someone burned on their behalf, for a total value of 100 ETH.

**Involvement in peg stability**

Availability of redemptions in the protocol depends on the levels of osETH position health relative to the redemption threshold in 90% LTV Vaults, and the price of osETH on the exchanges. If the price on exchanges deviates from the fair exchange rate by more than **\[value TBC]**, StakeWise Oracles will automatically exit a number of validators from the Vaults where positions exceed the redemption threshold.&#x20;

Oracles will sort such 90% LTV Vaults based on the total amount of ETH that can be redeemed (based on positions above the redemption threshold) and exit the required number of validators to take these osETH positions to a healthy level. The exited validators will provide sufficient ETH for the volume of osETH redemption that is expected to return the price back to the fair exchange rate.
{% endtab %}

{% tab title="osGNO" %}
StakeWise makes its best efforts to ensure that the value of osGNO on the exchanges corresponds to its fair exchange rate. The ability to receive GNO in exchange for osGNO at the fair exchange rate is the key mechanism to ensure price stability, and relies on the redemption mechanism.

The osGNO redemption mechanism allows anyone to redeem osGNO natively via StakeWise for its underlying value (staked GNO backing the osGNO tokens). Redemption happens when users burn osGNO they acquired on the exchanges and withdraw GNO backing from Vaults at the fair osGNO exchange rate.

The process of redeeming osGNO reduces the osGNO positions of certain stakers in Vaults, allowing them to improve their position health without manual actions. If the value of a user's osGNO position in the 90% LTV Vault reaches 91.5% of their staked GNO value, anyone can step in and burn a certain amount of osGNO from their position in exchange for redeeming a fair amount of GNO backing from the Vault.&#x20;

The amount is determined by the osGNO exchange rate and the amount of osGNO burned using the following formula:

**90% LTV Vaults**

{% code overflow="wrap" %}
```
Amount of osGNO to be redeemed = 10 * amount of osGNO currently minted - 9 * amount of GNO staked / osGNO exchange rate
```
{% endcode %}

The 91.5% level for initiating redemptions is known as the **redemption threshold** and is set by the StakeWise DAO.

Note that users always have the ability to improve their position health to avoid redemption.

**99.95% Vaults**

In a 99.95% LTV Vault, your position is always considered healthy because osGNO APY matches the APY of the lowest-yielding 99.95% LTV Vault. This ensures that your Vault's APY is never lower than osGNO's APY. Thus, maintaining the stability of your position.

[<mark style="color:blue;">Read our guide about maintaining a healthy osGNO position -></mark>](https://docs.stakewise.io/guides/ostoken#maintaining-a-healthy-ostoken-position)

In 90% LTV Vaults, there is a limit to how much osGNO can be burned from any given osGNO position. This amount is defined by the amount of osGNO that must be redeemed in order to bring a user's osGNO position health back to a healthy level (90%). Redemptions also don't incur any fees, have no economic impact on the users in Vaults, and don't expose those who redeem osGNO to adverse Vault performance or slashing.

**90% LTV Vault Example**

User has minted 87.238 osGNO that is now worth 91.6 GNO against a staked GNO position that is currently worth 100 GNO. The user's position is open to redemption because the value of minted osGNO relative to their GNO stake exceeds the redemption threshold, i.e. 91.5%.&#x20;

Users who bought osGNO on exchanges will use a portion of the position to redeem their osGNO, with the amount based on the osGNO exchange rate. If the osGNO exchange rate is currently 1.05 GNO/osGNO, users would be able to redeem 10 \* 87.238 - 9 \* 100 / 1.05 = 15.238 osGNO for 16 GNO, bringing the position back down to 90% of the staked GNO value.&#x20;

**Impact on users in 90% LTV Vaults**

osGNO redemptions do not lead to stakers in Vaults losing their capital. When someone burns a portion of a staker's minted osGNO on their behalf, the staker gets to keep the proportional amount of osGNO, without the need to burn it to fully unstake from the Vault. It is equivalent to simply buying that portion of osGNO on the exchange.&#x20;

Meanwhile, the health of users' remaining osGNO positions improves with redemptions.&#x20;

_Example_: a user starts off with 87.238095 osGNO minted and 100 GNO staked in the Vault, which implies a 1.05 GNO/osGNO exchange rate. Their osGNO position is worth 91.6% of their staked GNO value, triggering a redemption. 15.238095 osGNO is redeemed for 16 GNO, reducing the staker's outstanding minted osGNO from 87.238095 to 72, and their stake in the Vault from 100 to 84. As a result, osGNO position health improves to 90% of their staked GNO value. The user can claim 84 staked GNO from the Vault by burning 72 osGNO, and gets to keep the 15.238095 osGNO that someone burned on their behalf, for a total value of 100 GNO.

**Involvement in peg stability**

Availability of redemptions in the protocol depends on the levels of osGNO position health relative to the redemption threshold in 90% LTV Vaults, and the price of osGNO on the exchanges. If the price on exchanges deviates from the fair exchange rate by more than **\[value TBC]**, StakeWise Oracles will automatically exit a number of validators from the Vaults where positions exceed the redemption threshold.&#x20;

Oracles will sort such 90% LTV Vaults based on the total amount of GNO that can be redeemed (based on positions above the redemption threshold) and exit the required number of validators to take these osGNO positions to a healthy level. The exited validators will provide sufficient GNO for the volume of osGNO redemption that is expected to return the price back to the fair exchange rate.
{% endtab %}
{% endtabs %}

#### Liquidation mechanism

{% tabs %}
{% tab title="osETH" %}
**90% LTV Vaults**

StakeWise must maintain excess backing for osETH to ensure that permissionless minting of the token is safe for all osETH holders. A mechanism responsible for this is called the liquidation mechanism, where osETH positions that threaten the excess backing of osETH are forcibly closed and a penalty is applied to a user's stake to discourage such malicious behaviour.&#x20;

The liquidation mechanism kicks in if a user's minted osETH value exceeds 92% of their staked ETH value in the Vault. At this moment, their osETH position will be unhealthy, and anyone will be able to step in to burn the entire amount of osETH a staker has previously minted, in exchange for the underlying ETH and a 1% reward on the value of ETH redeemed. The reward to the liquidator is taken from the user's stake, which can be considered a 1% penalty to the user's stake in the Vault if their osETH position is liquidated.&#x20;

The 92% threshold at which the osETH position enters a liquidation is set by the DAO and is called the **liquidation threshold**. The DAO also sets the 1% reward for liquidating an osETH position and is called the **liquidation premium**.&#x20;

Note that users always have the ability to improve their position health to avoid liquidation.

**99.99% LTV Vaults**&#x20;

In a 99.99% LTV Vault, your position is always considered healthy because osETH APY matches the APY of the lowest-yielding 99.99% LTV Vault. This ensures that your Vault's APY is never lower than osETH's APY. Thus, maintaining the stability of your position and avoiding liquidations.

[<mark style="color:blue;">Read our guide about maintaining a healthy osETH position -></mark>](https://docs.stakewise.io/guides/ostoken#maintaining-a-healthy-ostoken-position)

**90% LTV Vaults**

Liquidators who close others' osETH positions receive the underlying value of osETH they burned plus a 1% liquidation premium in ETH from the Vault. StakeWise Oracles automatically exit enough validators in the Vault to facilitate the liquidation of unhealthy positions. Exited ETH will be used for returning the underlying value of osETH burned by the liquidators and payment of the 1% liquidation premium. Mechanically, this means liquidators can liquidate a position as soon as there is unbonded ETH in the Vault.&#x20;

In case the liquidation is triggered by a slashing event, it will take 36 days from the initial violation to exit the slashed validators, at which step the liquidators can step in.&#x20;

_Example:_ user has minted osETH that is now worth 92.01 ETH against a staked ETH position that is currently worth 100 ETH. The user's position is open to liquidation because the value of minted osETH relative to their ETH stake exceeds the liquidation threshold, i.e. is >92%. Users who bought osETH on exchanges will liquidate the position by burning osETH and redeeming ETH based on the fair osETH exchange rate, plus the 1% liquidation premium. If the osETH exchange rate is currently 1.05 ETH/osETH, users would be able to liquidate 87.6285714286 osETH for 92.9301 ETH, which includes 0.9201 ETH as the liquidation premium.

**Impact on users in 90% LTV Vaults**

osETH liquidations lead to a 1% penalty applied to the stake of liquidated users.&#x20;

When someone burns a staker's minted osETH on their behalf, the staker gets to keep the proportional amount of osETH without the need to burn it to fully unstake from the Vault. It is equivalent to simply buying that portion of osETH on the exchange. However, the user's remaining stake in the Vault is reduced by the 1% liquidation penalty.&#x20;

_Example_: a user starts off with 87.62857 osETH minted and 100 ETH staked in the Vault, which implies a 1.05 ETH/osETH exchange rate. Their osETH position is worth 92.01% of their staked ETH value, triggering a liquidation. 87.62857 osETH is redeemed for 92.9301 ETH (includes 0.9201 ETH as the liquidation premium), reducing a staker's outstanding minted osETH to 0, and their stake in the Vault from 100 to 7.0699 ETH. The user can claim 7.0699 staked ETH from the Vault at any time, and get to keep the 87.62857 osETH they originally minted, for a total value of 99 ETH.

**90% LTV Vaults' involvement in peg stability**

The liquidation mechanism ensures that osETH tokens always remain overcollateralized, helping to maintain the price of osETH on exchanges at par with the fair exchange rate. &#x20;
{% endtab %}

{% tab title="osGNO" %}
**90% LTV Vaults**

StakeWise must maintain excess backing for osGNO to ensure that permissionless minting of the token is safe for all osGNO holders. A mechanism responsible for this is called the liquidation mechanism, where osGNO positions that threaten the excess backing of osGNO are forcibly closed and a penalty is applied to a user's stake to discourage such malicious behaviour.

The liquidation mechanism kicks in if a user's minted osGNO value exceeds 92% of their staked GNO value in the Vault. At this moment, their osGNO position will be unhealthy, and anyone will be able to step in to burn the entire amount of osGNO a staker has previously minted, in exchange for the underlying GNO and a 1% reward on the value of GNO redeemed. The reward to the liquidator is taken from the user's stake, which can be considered a 1% penalty to the user's stake in the Vault if their osGNO position is liquidated.

The 92% threshold at which the osGNO position enters a liquidation is set by the DAO and is called the liquidation threshold. The DAO also sets the 1% reward for liquidating an osGNO position and is called the liquidation premium.

Note that users always have the ability to improve their position health to avoid liquidation.

**99.95% LTV Vaults**

In a 99.99% LTV Vault, your position is always considered healthy because osGNO APY matches the APY of the lowest-yielding 99.95% LTV Vault. This ensures that your Vault's APY is never lower than osGNO's APY. Thus, maintaining the stability of your position and avoiding liquidations.

[Read our guide about maintaining a healthy osGNO position ->](https://docs.stakewise.io/guides/ostoken#maintaining-a-healthy-ostoken-position)

**90% LTV Vaults**

Liquidators who close others' osGNO positions receive the underlying value of osGNO they burned plus a 1% liquidation premium in GNO from the Vault. StakeWise Oracles automatically exit enough validators in the Vault to facilitate the liquidation of unhealthy positions. Exited GNO will be used for returning the underlying value of osGNO burned by the liquidators and payment of the 1% liquidation premium. Mechanically, this means liquidators can liquidate a position as soon as there is unbonded GNO in the Vault.

In case the liquidation is triggered by a slashing event, it will take 36 days from the initial violation to exit the slashed validators, at which step the liquidators can step in.

_Example:_ user has minted osGNO that is now worth 92.01 GNO against a staked GNO position that is currently worth 100 GNO. The user's position is open to liquidation because the value of minted osGNO relative to their GNO stake exceeds the liquidation threshold, i.e. is >92%. Users who bought osGNO on exchanges will liquidate the position by burning osGNO and redeeming GNO based on the fair osGNO exchange rate, plus the 1% liquidation premium. If the osGNO exchange rate is currently 1.05 GNO/osGNO, users would be able to liquidate 87.6285714286 osGNO for 92.9301 GNO, which includes 0.9201 GNO as the liquidation premium.

**Impact on users in 90% LTV Vaults**

osGNO liquidations lead to a 1% penalty applied to the stake of liquidated users.

When someone burns a staker's minted osGNO on their behalf, the staker gets to keep the proportional amount of osGNO without the need to burn it to fully unstake from the Vault. It is equivalent to simply buying that portion of osGNO on the exchange. However, the user's remaining stake in the Vault is reduced by the 1% liquidation penalty.

_Example:_ a user starts off with 87.62857 osGNO minted and 100 GNO staked in the Vault, which implies a 1.05 GNO/osGNO exchange rate. Their osGNO position is worth 92.01% of their staked GNO value, triggering a liquidation. 87.62857 osGNO is redeemed for 92.9301 GNO (includes 0.9201 GNO as the liquidation premium), reducing a staker's outstanding minted osGNO to 0, and their stake in the Vault from 100 to 7.0699 GNO. The user can claim 7.0699 staked GNO from the Vault at any time, and get to keep the 87.62857 osGNO they originally minted, for a total value of 99 GNO.

**90% LTV Vaults' involvement in peg stability**

The liquidation mechanism ensures that osGNO tokens always remain overcollateralized, helping to maintain the price of osGNO on exchanges at par with the fair exchange rate.
{% endtab %}
{% endtabs %}
