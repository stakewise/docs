---
description: The page will guide you through setting up vault with DVT cluster.
---

# Running operator with DVT

### Prerequisites

Vault should be created in [Stakewise web UI](https://app.stakewise.io/).

### Step 1. Generate validator key shares

There are 2 ways to create validator keys:

* create keys alone
* create keys with a group using Distributed Key Generation (DKG) ceremony

Creating keys alone may be an option if you don't collaborate with anybody. In this case DVT still may be used for additional robustness. When using SSV you can fully delegate validator duties to other entities (SSV operators) and do not mind running validators on your own. See [Obol page](obol-setup.md) and [SSV page](ssv-setup.md) for further instructions if you are creating keys alone.

DKG is more secure and decentralized way because nobody has full control over validator keys. The document below is dedicated to DKG way.

{% tabs %}
{% tab title="Obol" %}
Generate validator keys with a group using DKG ceremony. See [Obol DKG guide](https://docs.obol.org/docs/start/quickstart\_group).
{% endtab %}

{% tab title="SSV" %}
Generate validator keys with a group using DKG ceremony. See [SSV DKG guide](https://docs.ssv.network/validator-user-guides/validator-management/distributing-a-validator-1).
{% endtab %}
{% endtabs %}

### Step 2. Set up DVT cluster

During cluster setup keep in mind:

* `withdrawal_address` should equal to vault address
* validator fee recipient should equal to address specified in vault details section on the vault page.

{% tabs %}
{% tab title="Obol" %}
Each DVT operator should run Charon instance. Charon is HTTP middleware built by Obol to enable any existing Ethereum validator clients to operate together as part of a distributed validator. Guide from step 1 includes setting up Charon.
{% endtab %}

{% tab title="SSV" %}
SSV node works as DVT replacement for validator client. Each SSV operator participating in a cluster should run his own node. See [the guide for SSV operators](https://docs.ssv.network/operator-user-guides/operator-node).
{% endtab %}
{% endtabs %}

### Step 3. Set up DVT sidecars

Run [DVT sidecar](https://github.com/stakewise/dvt-operator-sidecar) instance for each DVT node in a cluster. Each DVT operator should run his own sidecar instance.

Instructions how to run single sidecar for a given DVT operator is below.

{% tabs %}
{% tab title="Obol" %}
DVT sidecar should have access to Obol node directory generated on step 1. Node directory contains cluster lock file and validator keys. In example below `~/node0` is used as node directory.

Fill .env file with environment variables.
{% endtab %}

{% tab title="SSV" %}
Sidecar should have access to:

* SSV operator key file and password file generated on step 2
* keyshares json file generated on step 1

Put these files into `~/ssv-data` directory which will be mapped as docker volume.
{% endtab %}
{% endtabs %}

<details>

<summary>Env example for Obol</summary>

```ini
# Network choices: mainnet,holesky,gnosis,chiado
NETWORK=mainnet

# LOG_LEVEL=INFO
# LOG_FORMAT=plai
# SENTRY_DSN=
# SENTRY_ENVIRONMENT=

# Relayer API params
RELAYER_ENDPOINT=https://mainnet-dvt-relayer.stakewise.io
RELAYER_TIMEOUT=10

# Interval for polling DVT Relayer
POLL_INTERVAL=1

# Cluster type. Choices: OBOL, SSV
CLUSTER_TYPE=OBOL

# Path to Obol keystores directory.
OBOL_KEYSTORES_DIR=/node0/validator_keys

# Obol cluster lock file path
OBOL_CLUSTER_LOCK_FILE=/node0/cluster-lock.json

# Obol node index
# Usually node index is a part of keystore path: node0, node1...
OBOL_NODE_INDEX=0
```

</details>

<details>

<summary>Env example for SSV</summary>

```ini
# Network choices: mainnet,holesky,gnosis,chiado
NETWORK=mainnet

# LOG_LEVEL=INFO
# LOG_FORMAT=plain

# SENTRY_DSN=
# SENTRY_ENVIRONMENT=

# Relayer API params
RELAYER_ENDPOINT=https://mainnet-dvt-relayer.stakewise.io
RELAYER_TIMEOUT=10

# Interval for polling DVT Relayer
POLL_INTERVAL=1

# Cluster type. Choices: OBOL, SSV
CLUSTER_TYPE=SSV

# SSV operator key
# Path to key file
SSV_OPERATOR_KEY_FILE=/data/encrypted_private_key.json
# Path to password file
SSV_OPERATOR_PASSWORD_FILE=/data/password.txt

# SSV operator id (node id)
SSV_OPERATOR_ID=123

# SSV keyshares file path
SSV_KEYSHARES_FILE=/data/keyshares.json
```

</details>

Run sidecar:

{% tabs %}
{% tab title="Obol" %}
```bash
docker run \
-u $(id -u):$(id -g) \
--env-file .env \
-v ~/node0:/node0 \
europe-west4-docker.pkg.dev/stakewiselabs/public/dvt-operator-sidecar:v0.2.0
```
{% endtab %}

{% tab title="SSV" %}
```bash
docker run \
-u $(id -u):$(id -g) \
--env-file .env \
-v ~/ssv-data:/data \
europe-west4-docker.pkg.dev/stakewiselabs/public/dvt-operator-sidecar:v0.2.0
```
{% endtab %}
{% endtabs %}

### Step 4. Set up Stakewise Operator

Single operator instance should be set up for DVT cluster.&#x20;

#### Step 4.0 Prerequisites

Ensure [prerequisites](https://docs.stakewise.io/for-operators/operator-service#prerequisites) are satisfied. This includes setting up execution client and consensus client.

#### Step 4.1 Generate mnemonic

Run [init](https://docs.stakewise.io/for-operators/operator-service#step-1.-create-mnemonic) command. The command creates mnemonic and creates folders structure. Mnemonic will not be used to generate validator keys because validator keys are already created by DVT tools (step 1). Mnemonic may be used for creating wallet (see below).&#x20;

#### Step 4.2 **Create hot wallet**

Run the [create-wallet](https://docs.stakewise.io/for-operators/operator-service#step-3.-create-hot-wallet) command to create your hot wallet using your mnemonic (note, this mnemonic can be the one generated on step 4.1, or a new mnemonic if you desire).

Note, you must send some ETH (or xDAI for Gnosis) to the wallet for gas expenses

#### Step 4.3 Upload deposit data file to Vault

DKG ceremony produces deposit data file in addition to keystores. See [instructions](https://docs.stakewise.io/for-operators/operator-service#upload-deposit-data-file-to-vault) for uploading this file to Vault.

#### Step 4.3 Run Stakewise Operator

See [instructions](https://docs.stakewise.io/for-operators/operator-service#upload-deposit-data-file-to-vault).&#x20;

There are some changes for DVT case:

* Run operator with `start-api` command, unlike `start` command in default scenario.
* Pass `--relayer-type=DVT --relayer-endpoint=https://mainnet-dvt-relayer.stakewise.io/` in `start-api` options
* Pass `--deposit-data-path` to provide deposit data file generated during DKG