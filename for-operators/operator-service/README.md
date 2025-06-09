---
description: >-
  Learn how to configure the Operator Service to become a node operator on
  StakeWise V3.
cover: ../../.gitbook/assets/Frame 27513376 (1).png
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

# Operator Service

All node operators of StakeWise V3 must run Operator Service in order to successfully register validators on the platform. The below 4-step guide walks you through the initial setup of Stakewise Operator Service.

### Prerequisites

#### Execution client

Ensure your execution node is fully synced and running. Any execution client that supports [ETH Execution API specification](https://ethereum.github.io/execution-apis/category/reference/) can be used:

* [Nethermind](https://launchpad.ethereum.org/en/nethermind) (Ethereum, Gnosis)
* [Besu](https://launchpad.ethereum.org/en/besu) (Ethereum)
* [Erigon](https://launchpad.ethereum.org/en/erigon) (Ethereum, Gnosis)
* [Geth](https://launchpad.ethereum.org/en/geth) (Ethereum)
* [Reth](https://github.com/paradigmxyz/reth) (Ethereum)

**Special configuration for Erigon and Reth**

{% tabs %}
{% tab title="Reth" %}
The problem with Reth could be event logs pruning. Operator reads event logs from certain contracts. In order to preserve those logs execution client needs to be tweaked.&#x20;

The required setting in the `reth.toml` is:

```
[prune.segments.receipts_log_filter.0x6b5815467da09daa7dc83db21c9239d98bb487b5]
before = 21471500
```

Here `0x6b5815467da09daa7dc83db21c9239d98bb487b5` is Keeper contract address on Ethereum Mainnet. Note that the address must be lowercased.

For other networks you have to adjust Keeper address and block number. You can find Keeper address on [Networks](../../for-developers/networks/) page. You can look up the Keeper contract's block number in a block explorer, e.g., Etherscan. Use the contract creation block number.&#x20;

Alternatively if you want to save more disk space you can use the block when protocol config was updated. Actual values are defined in [network config](https://github.com/stakewise/v3-operator/blob/master/src/config/networks.py) in Operator sources. See `CONFIG_UPDATE_EVENT_BLOCK` field for selected network.
{% endtab %}

{% tab title="Erigon" %}
The problem with Erigon could be event logs pruning. Operator reads event logs from certain contracts. In order to preserve those logs execution client needs to be tweaked. &#x20;

The required flags for Erigon on Ethereum Mainnet:

```
erigon --prune=receipts --prune.to=21471500
```

For other networks you have to adjust the block number. You can look up the Keeper contract's block number in a block explorer, e.g., Etherscan. Use the contract creation block number.

Alternatively if you want to save more disk space you can use the block when protocol config was updated. Actual values are defined in [network config](https://github.com/stakewise/v3-operator/blob/master/src/config/networks.py) in Operator sources. See `CONFIG_UPDATE_EVENT_BLOCK` field for selected network.
{% endtab %}
{% endtabs %}



#### Consensus client

Ensure your consensus node is fully synced and running. Any consensus client that supports [ETH Beacon Node API specification](https://ethereum.github.io/beacon-APIs/#/) can be used:

* [Lighthouse](https://launchpad.ethereum.org/en/lighthouse) (Ethereum, Gnosis)
* [Nimbus](https://launchpad.ethereum.org/en/nimbus) (Ethereum, Gnosis)
* [Prysm](https://launchpad.ethereum.org/en/prysm) (Ethereum)
* [Teku](https://launchpad.ethereum.org/en/teku) (Ethereum, Gnosis)
* [Lodestar](https://launchpad.ethereum.org/en/lodestar) (Ethereum, Gnosis)

#### Vault

You must have a deployed Vault. You can create a new Vault or use an existing one. To create a new Vault:

1. Go to [Operate page](https://app.stakewise.io/operate).
2. Connect with your wallet in upper right corner, then click on "Create Vault".
3. Process vault setup step by step.
4. Once vault is deployed go to its page.

{% hint style="info" %}
You can find the vault address either in the URL bar or in the "Contract address" field by scrolling to the "Details" at the bottom of the page. The vault address is used in the following sections.
{% endhint %}

### Install Operator Service

Operator Service can be run via a binary, docker image, deployed on a Kubernetes cluster using the Operator Helm Chart, or built from source. Decide on your preferred method and follow the respective instructions below.

{% tabs %}
{% tab title="Binary" %}
Head to the [releases page](https://github.com/stakewise/v3-operator/releases) to find the latest version of Operator Service. Identify the binary file specific to your node hardware, download and decompress it.

You will execute Operator Service commands from within the `v3-operator` folder using the below format (note that the use of flags is optional):

```
./operator COMMAND --flagA=123 --flagB=xyz
```

**Install script (Linux and macOS)**

To install a binary for the latest release, run:

```bash
curl -sSfL https://raw.githubusercontent.com/stakewise/v3-operator/master/scripts/install.sh | sh -s
```

The binary will be installed inside the \~/bin directory. Add the binary to your path:

```bash
export PATH=$PATH:~/bin
```

If you want to install a specific version to a custom location, run:

```bash
curl -sSfL https://raw.githubusercontent.com/stakewise/v3-operator/master/scripts/install.sh | sh -s -- -b <custom_location> vX.X.X
```
{% endtab %}

{% tab title="Docker Image" %}
_In the context of running an Operator Service through Docker, it is crucial to ensure that the `--data-dir` flag is used in all calls. This flag provides a directory path where essential data for the Operator Service is read from or written to, allowing for a persistent data storage mechanism across Docker container instances._

Pull the latest docker operator docker image:

```bash
docker pull europe-west4-docker.pkg.dev/stakewiselabs/public/v3-operator:v3.1.5
```

You can also build the docker image from source by cloning this repo and executing the following command from within the `v3-operator` folder:

```bash
docker build --pull -t europe-west4-docker.pkg.dev/stakewiselabs/public/v3-operator:v3.1.5 .
```

You will execute Operator Service commands using the format below (note the use of flags are optional):

```bash
docker run --rm -ti \
-u $(id -u):$(id -g) \
-v ~/.stakewise/:/data \
europe-west4-docker.pkg.dev/stakewiselabs/public/v3-operator:v3.1.5 \
src/main.py COMMAND \
--data-dir=/data \
--flagA=123 \
--flagB=xyz
```
{% endtab %}

{% tab title="Source Files" %}
Build requirements:

* [Python 3.10+](https://www.python.org/downloads/)
* [Poetry](https://python-poetry.org/docs/)

Clone this repo and install dependencies by executing the following command from within the `v3-operator` folder:

```bash
poetry install --only main
```

You will execute Operator Service commands from within the `v3-operator` folder using the below format (note that the use of flags is optional):

```bash
PYTHONPATH=. poetry run python src/main.py COMMAND --flagA=123 --flagB=xyz
```
{% endtab %}

{% tab title="Kubernetes (advanced)" %}
A separate guide runs through the set-up of Operator Service via Kubernetes, designed to run large numbers of validators (up to 10,000). Visit the [Kubernetes setup](https://docs.stakewise.io/for-operators/kubernetes-staking-setup) for more details.
{% endtab %}
{% endtabs %}

### Prepare Operator Service

In order to run Operator Service, you must first create keystores and deposit data file for your Vault's validators, and set up a hot wallet for Operator Service to handle validator registrations.

Operator Service has in-built functionality to generate all of the above, or you are free to use your preferred methods of generating keystores and deposit data file, such as via [Wagyu Keygen](https://github.com/stake-house/wagyu-key-gen), and your preferred tool for generating the hot wallet, such as [MetaMask](https://metamask.io/) or [MyEtherWallet](https://help.myetherwallet.com/en/articles/6512619-using-mew-offline-current-mew-version-6).

{% hint style="warning" %}
Note, the deposit data file must be created using the Vault contract as the withdrawal address. You can find the Vault address either via the URL bar of your Vault page or in the "Contract address" field by scrolling to the "Details" section at the bottom of the Vault page.
{% endhint %}

The below steps walk you through this set-up using Operator Service:

#### **Step 1. Create mnemonic**

Run the `init` command and follow the steps to set up your mnemonic used to derive validator keys. For example, if running Operator Service from binary, you would use:

```sh
./operator init
```

<details>

<summary>Example output</summary>

```
Enter the network name (mainnet, holesky) [mainnet]:
Enter your vault address: 0x3320a...68
Choose your mnemonic language (chinese_simplified, chinese_traditional, czech, english, italian, korean, portuguese, spanish) [english]:
This is your seed phrase. Write it down and store it safely, it is the ONLY way to recover your validator keys.

pumpkin anxiety private salon inquiry ....


Press any key when you have written down your mnemonic.

Please type your mnemonic (separated by spaces) to confirm you have written it down

: pumpkin anxiety private salon inquiry ....

done.
Successfully initialized configuration for vault 0x3320a...68
```

</details>

#### **Step 2. Create validator keys**

Next, run the `create-keys` command to kickstart the deposit data and validator keystores creation process, making sure you have your newly created mnemonic to hand:

```bash
./operator create-keys
```

<details>

<summary>Example output</summary>

```
Enter the vault address: 0x3320a...68
Enter the number of the validator keys to generate: 10
Enter the mnemonic for generating the validator keys: pumpkin anxiety private salon inquiry ....
Creating validator keys:    [####################################]  10/10
Generating deposit data JSON    [####################################]  10/10
Exporting validator keystores    [####################################]  10/10

Done. Generated 10 keys for 0x3320a...68 vault.
Keystores saved to /home/user/.stakewise/0x3320a...68/keystores file
Deposit data saved to /home/user/.stakewise/0x3320a...68/keystores/deposit_data.json file
```

</details>

You may not want the operator service to have direct access to the validator keys. Validator keystores do not need to be present directly in the operator. You can check the [remote signer](https://docs.stakewise.io/for-operators/operator-service/running-with-remote-signer) or [Hashicorp Vault](https://docs.stakewise.io/for-operators/operator-service/running-with-hashi-vault) guides on how to run Operator Service with them.

{% hint style="info" %}
Remember to upload the newly generated validator keys to the validator(s). For that, please follow a guide for your consensus client. The password for your keystores is located in the `password.txt` file in the keystores folder.
{% endhint %}

#### **Step 3. Create hot wallet**

Run the `create-wallet` command to create your hot wallet using your mnemonic (note, this mnemonic can be the same as the one used to generate the validator keys, or a new mnemonic if you desire).

```bash
./operator create-wallet
```

<details>

<summary>Example output</summary>

```
Enter the vault address: 0x3320a...68
Enter the mnemonic for generating the wallet: pumpkin anxiety private salon inquiry ...
Done. The wallet and password saved to /home/user/.stakewise/0x3320a...68/wallet directory. The wallet address is: 0x239B...e3Cc
```

</details>

{% hint style="warning" %}
Note, you must send some ETH (or xDAI for Gnosis) to the wallet for gas expenses. Each validator registration costs around 0.01 ETH with 30 Gwei gas price. You must keep an eye on your wallet balance, otherwise validators will stop registering if the balance falls too low.
{% endhint %}

### Upload deposit data file to Vault

Once you have created your validator keys, deposit data file, and hot wallet, you need to upload the deposit data file to the Vault. This process connects your node to the Vault. Note, if there is more than one node operator in a Vault, you first need to merge all operator deposit data files into a single file (use the merge-deposit-data command). Uploading the deposit data file can be achieved either through the StakeWise UI or via Operator Service and can only be done by the [Vault Admin or Keys Manager](https://docs.stakewise.io/protocol-overview-in-depth/vaults#governance-and-management).

{% tabs %}
{% tab title="StakeWise UI" %}
1. Connect with your wallet and head to the [Operate page](https://app.stakewise.io/operate).
2. Select the Vault you want to upload the deposit data file to.
3. In the upper right corner, click on "Settings" and open the "Deposit Data" tab. The "Settings" button is only visible to the Vault Admin or Keys Manager.
4. Upload the deposit data file either by dragging and dropping the file, or clicking to choose the file via your file browser.
5. Click Save and a transaction will be created to sign using your wallet. The Vault's deposit data file will be uploaded when the transaction is confirmed on the network.
{% endtab %}

{% tab title="Operator Service" %}
If for some reason uploading deposit data using UI is not an option. You can calculate deposit data Merkle tree root with the following command:

```bash
./operator get-validators-root
```

```
Enter the vault address: 0xeEFFFD4C23D2E8c845870e273861e7d60Df49663
The validator deposit data Merkle tree root: 0x50437ed72066c1a09ee85978f168ac7c58fbc9cd4beb7962c13e68e7faac26d7
```

Find out your Vault version by calling `version` method of Vault contract.

For Vaults version 1 call `setValidatorsRoot` method of Vault contract.

For Vaults version 2 or higher call `setDepositDataRoot` method of `DepositDataRegistry` contract.

Below shows the steps to do this via Etherscan, but the same can be achieved via CLI if you prefer ( using [eth-cli](https://github.com/protofire/eth-cli) and `eth contract:send` for example). Note, the ABI of the `DepositDataRegistry` contract can be found [here](https://github.com/stakewise/v3-core/blob/v3.0.0/abi/IDepositDataRegistry.json).

1. Head to Deposit Data Registry contract address page on Etherscan in your browser. You will find `DepositDataRegistry` contract [here](https://etherscan.io/address/0x75AB6DdCe07556639333d3Df1eaa684F5735223e) for Ethereum and [here](https://gnosisscan.io/address/0x58e16621B5c0786D6667D2d54E28A20940269E16) for Gnosis.
2. Select the Contract tab and then Write Contract.
3. Connect your wallet to Etherscan (note this must be either the Vault Admin or Deposit Data Manager).
4. Find the `setDepositDataRoot` function and click to reveal the drop-down.
5. Enter your Vault address. Enter your Merkle tree root returned from the command. Click Write.
6. Confirm the transaction in your wallet to finalize the deposit data upload to your Vault.
{% endtab %}
{% endtabs %}

### Run Operator Service

You are ready to run the Operator Service using the `start` command, optionally passing your Vault address and consensus and execution endpoints as flags.

If you **did not** use Operator Service to generate hot wallet, you will need to add the following flags:

* `--hot-wallet-file` - path to the password-protected _.txt_ file containing your hot wallet private key.
* `--hot-wallet-password-file` - path to a _.txt_ file containing the password to open the protected hot wallet private key file.

If you **did not** use Operator Service to generate validator keys, you will need to add the following flag:

* `--keystores-dir` - The directory with validator keys in the EIP-2335 standard. The folder must contain either a single `password.txt` password file for all the keystores or separate password files for each keystore with the same name as keystore, but ending with `.txt`. For example, `keystore1.json`, `keystore1.txt`, etc.

If you **did not** use Operator Service to generate deposit data file, or you use combined deposit data file from multiple operators, you will need to add the following flag:

* `--deposit-data-file` - Path to the deposit data file (Vault directory is default).

{% tabs %}
{% tab title="Binary" %}
You can start the operator service using binary with the following command:

```bash
./operator start \
    --vault=0x000... \
    --consensus-endpoints=http://localhost:5052 \
    --execution-endpoints=http://localhost:8545
```
{% endtab %}

{% tab title="Docker" %}
For docker, you first need to mount the folder containing validator keystores and deposit data file generated into the docker container. You then need to also include the `--data-dir` flag alongside the `start` command as per the below:

```bash
docker run --restart on-failure:10 \
-u $(id -u):$(id -g) \
-v ~/.stakewise/:/data \
europe-west4-docker.pkg.dev/stakewiselabs/public/v3-operator:v3.1.5 \
src/main.py start \
--vault=0x3320ad928c20187602a2b2c04eeaa813fa899468 \
--data-dir=/data \
--consensus-endpoints=http://localhost:5052 \
--execution-endpoints=http://localhost:8545
```
{% endtab %}

{% tab title="Source Files" %}
```
PYTHONPATH=. poetry run python src/main.py start \
--vault=0x000... \
--consensus-endpoints=http://localhost:5052 \
--execution-endpoints=http://localhost:8545
```
{% endtab %}
{% endtabs %}

{% hint style="success" %}
Congratulations, you should now have Operator Service up and running and ready to trigger validator registrations within your Vault!
{% endhint %}

### Other commands <a href="#user-content-misc-commands" id="user-content-misc-commands"></a>

Operator Service has many different commands that are not mandatory but might come in handy.

#### Add validator keys to Vault

You can always add more validator keys to your Vault. For that, you need to generate new validator keys and deposit data as described in [Step 2. Create validator keys](https://docs.stakewise.io/for-operators/operator-service#step-2.-create-validator-keys) and upload the deposit data file to your Vault as described in [Step 3. Upload deposit data file to Vault](https://docs.stakewise.io/for-operators/operator-service#upload-deposit-data-file-to-vault). Note, uploading a new deposit data file will overwrite the existing file and consequently overwrite previously un-used validator keys. It can be done at any point, but only by the Vault Admin or Keys Manager.

#### Validators voluntary exit

The validator exits are handled by oracles, but in case you want to force trigger exit your validators, you can run the following command:

```bash
./operator validators-exit
```

Follow the steps, confirming your consensus node endpoint, Vault address, and the validator indexes to exit.

<details>

<summary>Example output</summary>

```
Enter the comma separated list of API endpoints for consensus nodes: https://example.com
Enter your vault address: 0x3320ad928c20187602a2b2c04eeaa813fa899468
Are you sure you want to exit 3 validators with indexes: 513571, 513572, 513861? [y/N]: y
Validators 513571, 513572, 513861 exits successfully initiated
```

</details>

#### Update Vault state (Harvest Vault)

Updating the _Vault state_ distributes the Vault fee to the Vault fee address and updates each staker's position. If an ERC-20 token was chosen during Vault creation, the Vault specific ERC-20 reprices based on the rewards/penalties since the previous update and the Vault fees are distributed in newly minted ERC-20 tokens.

By default, each _Vault state_ gets updated whenever a user interacts with the Vault (deposit, withdraw, etc.), with a 12 hours cooldown. Vault state can also be updated by the Vault operator(s) by passing the `--harvest-vault` flag to the Operator Service `start` command. Harvest occurs every 12 hours and the gas fees are paid by the hot wallet linked to the Operator Service.

Harvesting the Vault rewards simplifies the contract calls to the Vault contract and reduces the gas fees for stakers, for example, the Vault does not need to sync rewards before calling deposit when a user stakes.

#### Merge deposit data files from multiple operators

You can use the following command to merge deposit data file:

```bash
./operator merge-deposit-data
```

#### Recover validator keystores

You can recover validator keystores that are active.

{% hint style="danger" %}
Make sure there are no validators running with recovered validator keystores and 2 epochs have passed, otherwise you can get slashed. For security purposes, make sure to protect your mnemonic as it can be used to generate your validator keys.
{% endhint %}

```bash
./operator recover
```

<details>

<summary>Example output</summary>

```
Enter the mnemonic for generating the validator keys: [Your Mnemonic Here]
Enter your vault address: 0x3320ad928c20187602a2b2c04eeaa813fa899468
Enter comma separated list of API endpoints for execution nodes: https://example.com
Enter comma separated list of API endpoints for consensus nodes: https://example.com
Enter the network name: goerli
Found 24 validators, recovering...
Generating keystores [####################################] 100%
Keystores for vault {vault} successfully recovered to {keystores_dir}
```

</details>

### Optional extras

#### Environment variables

Operator Service can be configured via environment variables instead of CLI flags. Copy [this example file](https://github.com/stakewise/v3-operator/blob/master/.env.example) and save it as `.env`. Run through the file, adjusting as and where necessary based on your node configuration.

Remember to load the environment variables before running Operator Service, for example:

```
export $(grep -v '^#' .env | xargs)
```

You can check the environment variables are set and loaded correctly by running `env`.

#### Max gas fee

To mitigate excessive gas costs, operators can pass the `--max-fee-per-gas-wei` flag when starting Operator Service (or configure this variable via [Environment Variables](./#environment-variables)) to set the maximum base fee they are happy to pay for both validator registrations and Vault harvests (if Operator is started using the `--harvest-vault` flag).

#### Reduce Operator Service CPU load

`--pool-size` can be passed as a flag with both `start` and `create-keys` commands. This flag defines the number of CPU cores that are used to both load keystores and create keystores. By default, Operator Service will use 100% of the CPU cores.

Setting `--pool-size` to `(number of CPU cores) / 2` is a safe way to ensure that Operator Service does not take up too much CPU load and impact node performance during the creation and loading of keystores.
