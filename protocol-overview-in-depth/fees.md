---
description: Learn about the fee structure in StakeWise V3
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

# Fees

StakeWise V3 is a liquid staking protocol that acts as a middleware between stakers and node operators.&#x20;

The protocol charges fees for the use of certain components, like osToken, and may provide other components completely free. The total fee a user is expected to pay will be the sum of fees applied for the use of different StakeWise V3 components. &#x20;

Explore the fee structure of StakeWise V3 below.&#x20;

### Vault staking fee

Every Vault charges stakers its own staking fee, applied to the network rewards earned by the Vault's validators.&#x20;

The fee can range from 0% to 100% of the network rewards. The fee level is set by the Vault creator at the moment of Vault's deployment and cannot be changed after the fact.&#x20;

The fee level for a given Vault can be found in the Details at the bottom of the Vault page (see the "Staking fee" section). &#x20;

The fee is automatically deducted when rewards are distributed, so the amount of network rewards users receive by staking in Vaults is already net of the staking fee.

StakeWise DAO does not charge Vault creators or stakers for the use of Vaults. Instead, Vault infrastructure is provided as a public good.

Stakers must familiarize themselves with the fee set by the Vault in which they plan to stake before depositing the funds.&#x20;

### osToken staking fee

{% tabs %}
{% tab title="osETH" %}
Stakers who mint osETH tokens against their stake in the Vault must pay the osETH staking fee, applied as a percentage of network rewards earned by osETH.&#x20;

StakeWise DAO charges a 5% fee on the rewards accumulated by osETH, and continuously applies the fee to the balance of osETH a user must return to the Vault.&#x20;

The fee is charged in osETH, meaning that the amount of osETH a user must return to the Vault constantly increases proportionately to the size of the fee.

_Example_: a user's minted osETH has accumulated 1 ETH in rewards on their stake. StakeWise will apply a 0.05 ETH fee to the user's osETH balance using the current osETH exchange rate. If the rate is 1.05 ETH/osETH, the user's total balance of minted osETH will increase by 0.05/1.05 = 0.04761904761 osETH.&#x20;
{% endtab %}

{% tab title="osGNO" %}
Stakers who mint osGNO tokens against their stake in the Vault must pay the osGNO staking fee, applied as a percentage of network rewards earned by osGNO.&#x20;

StakeWise DAO charges a 5% fee on the rewards accumulated by osGNO, and continuously applies the fee to the balance of osGNO a user must return to the Vault.&#x20;

The fee is charged in osGNO, meaning that the amount of osGNO a user must return to the Vault constantly increases proportionately to the size of the fee.

_Example_: a user's minted osGNO has accumulated 1 GNO in rewards on their stake. StakeWise will apply a 0.05 GNO fee to the user's osGNO balance using the current osGNO exchange rate. If the rate is 1.05 GNO/osGNO, the user's total balance of minted osGNO will increase by 0.05/1.05 = 0.04761904761 osGNO.&#x20;
{% endtab %}
{% endtabs %}
