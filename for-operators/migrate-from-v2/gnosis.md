# Gnosis

### Step 0. Download Operator

Download the latest operator binary from [here](https://github.com/stakewise/v3-operator/releases).

### Step 1. Validator keys recovery

Follow the steps to recover the keystores using your validator keys mnemonic [here](https://github.com/stakewise/v3-operator?tab=readme-ov-file#recover-validator-keystores).

After recovery add fake `deposit_data.json` file to your operator's vault directory, with content:

```
[{"pubkey": "aa8c737dd0b96232094c5591fa5a02b0e72e4292b6bbfd476673c3dbc56da996888d9d95724375b4ab3734172afec382", "withdrawal_credentials": "0100000000000000000000004b4406ed8659d03423490d8b62a1639206da0a7a", "amount": 32000000000, "signature": "a336744ac33a0329dbfe070b6b91a482386b22a7576aefd14d770d5e525b9b98539afa472dd1cb6399b801363d79fefd0a75929e290e3a16f9f57e27a2a6e98b8c7080a9a89b0b8ae86928abe20bbc298af894df24a7c25baab49bc992b99737", "deposit_message_root": "bafe0525dc543e89dcc2e1b22e68e6673b1f4dee9f5e82d9d65c77a5d012afc9", "deposit_data_root": "c32fdb0f6faced1b51a04b3bbb006d030399275ccf6dfc23e19cf3f0d5881250", "fork_version": "00000064", "network_name": "gnosis", "deposit_cli_version": "2.4.0"}]
```

#### Step 1.1. Import Genesis Keys (If applicable)

<mark style="color:red;">**If you run keys from the Verihash operator before continuing, you must import them.**</mark> This can be done with the following command:

<pre><code><strong>./operator \
</strong>   import-genesis-keys \
   --rsa-key /path/to/rsa_key \
   --exported-keys-dir /path/to/keys \
   --vault 0x4b4406ed8659d03423490d8b62a1639206da0a7a
</code></pre>

### Step 2. Setup operator database

Create new database called `operator` and the user for the database. Next, initialize database and upload keysotres:

```
./operator remote-db setup
Enter your vault address: 0x4b4406ed8659d03423490d8b62a1639206da0a7a
Enter the Postgres DB connection URL (e.g. postgresql://username:pass@hostname/dbname): postgresql://username:pass@hostname/dbname
Successfully configured remote database.
Encryption key: SAAHK4DYwAvWMcKpV........
NB! You must store your encryption in a secure cold storage!

./operator remote-db upload-keypairs
```

### Step 3. Start web3signer

To start web3signer, use our chart.  With `values.yaml`&#x20;

```
global:
    network: gnosis
    vault: 0x4b4406ed8659d03423490d8b62a1639206da0a7a
dbUrl: jdbc:postgresql://postgres:postgres@localhost/web3signer
dbUsername: web3signer
dbPassword: <password goes here>
dbKeystoreUrl: postgresql://postgres:postgres@localhost/operator
decryptionKey: <decrypt key goes here>
```

The deployment command looks like this:

```sh
helm repo add stakewise https://charts.stakewise.io
helm upgrade --install web3signer stakewise/web3signer \
  -n web3signer \
  -f values.yaml
```

### Step 4. Create wallet and Kubernetes secret

Сreate operator hot wallet by following the instructions [here](https://github.com/stakewise/v3-operator?tab=readme-ov-file#step-3-create-hot-wallet).

Before deploying v3-operator service create kubernetes secret with operator wallet:

```
kubectl create secret -n operator generic v3-operator-wallet-data \
  --from-file=/home/username/.stakewise/0x4b4406ed8659d03423490d8b62a1639206da0a7a/wallet
```

### Step 5. Start the Operator

To start the operator, use our chart. With `values.yaml`:&#x20;

```
settings:
    network: gnosis
    vault: 0x4b4406ed8659d03423490d8b62a1639206da0a7a
    executionEndpoints: https://node.example.com/gnosis-nethermind
    consensusEndpoints: https://node.example.com/gnosis-lighthouse
    walletSecretName: wallet-secret
    remoteDbConfig:
        enabled: true
        dbUrl: postgresql://postgres:postgres@localhost/operator
        remoteSignerUrl: http://web3signer.web3signer:6174
```

The deployment command looks like this:

```sh
helm repo add stakewise https://charts.stakewise.io
helm upgrade --install v3-operator stakewise/v3-operator \
  -n operator \
  -f values.yaml
```

### Step 6. Start the Validators

To start the validators, use our chart. With `values.yaml`:

```
global:
    network: gnosis
    vault: 0x4b4406ed8659d03423490d8b62a1639206da0a7a
dbKeystoreUrl: postgresql://postgres:postgres@localhost/operator
enabled: true
type: teku
validatorsCount: 1
suggestedFeeRecipient: 0x30db0d10d3774e78f8cB214b9e8B72D4B402488a
web3signerEndpoint: http://web3signer.web3signer:6174
beaconChainRpcEndpoints:
    - https://teku.example.com/
```

The deployment command looks like this:

```sh
helm repo add stakewise https://charts.stakewise.io
helm upgrade --install validators stakewise/web3signer-validators \
  -n validators \
  -f values.yaml
```

