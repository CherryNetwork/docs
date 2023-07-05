# Become a Validator

## Preliminaries

Running a validator on a live network is a lot of responsibility! You will be accountable for not only your own stake, but also the stake of your current nominators. If you make a mistake and get slashed, your money and your reputation will be at risk. However, running a validator can also be very rewarding, knowing that you contribute to the security of a decentralized network while growing your stash.

{% hint style="danger" %}
Warning: It is highly recommended that you have significant system administration experience before attempting to run your own validator.
{% endhint %}

## Initial Set-up

### Requirements

The most common way for a beginner to run a validator is on a cloud server running Linux. You may choose whatever [VPS](https://wiki.polkadot.network/docs/maintain-guides-how-to-validate-polkadot#vps-list) provider that your prefer, and whatever operating system you are comfortable with. For this guide we will be using **Ubuntu 18.04**, but the instructions should be similar for other platforms.

### Note Prerequisites: Install Rust & Dependencies

This command will fetch the latest version of Rust and install it.

```bash
curl https://sh.rustup.rs -sSf | sh -s -- -y
```

To configure your shell, run the following command.

```bash
source $HOME/.cargo/env
```

Finally, run this command to install the necessary dependencies for compiling and running the Cherry Node.

```bash
sudo apt update && sudo apt install -y git build-essential clang pkg-config protobuf-compiler curl libssl-dev llvm libudev-dev
rustup default stable
rustup update
rustup update nightly
rustup target add wasm32-unknown-unknown --toolchain nightly
```

### Building the `Cherry` binary

```bash
# Clone the cherry-relay-node GitHub Repository
git clone https://github.com/CherryNetwork/cherry-relay-node.git
cd cherry-relay-node
# Always build from cherry branch
git checkout cherry
cargo build --release
```

### Running the **`Cherry`** binary

{% hint style="info" %}
If you were running a node previously(especially if the node was not a validator) run the following for purging the previous chain: `./target/release/cherry purge-chain --chain node/service/chain-specs/mainnet-relay-regenesis.json -y` on Mainnet
or
`./target/release/cherry purge-chain --chain cherry-testnet -y` on Testnet
{% endhint %}

#### 1. Mainnet

Methods:

1. Binary:

   ```bash
   ./target/release/cherry --chain node/service/chain-specs/mainnet-relay-regenesis.json \
	--name "<insert a name of your choice for your validator>" \
	--bootnodes /ip4/13.39.104.56/tcp/30333/p2p/12D3KooWJmNgQE6hftytjeXnwNRNrkxFLoChSa5FSuU7F4DnBUEZ \
	--validator --base-path=/tmp/cherry-mainnet \
	--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
	--rpc-methods=unsafe \
	--rpc-cors all \
	--rpc-external \
	--ws external
   ```

2. Docker

	```bash
	docker run --rm -it -p 9944:9944 -p 9933:9933 -p 30333:30333 -v $(pwd):/tmp/cherry-node cherrylabsorg/cherry-polkadot-node:dev --chain cherry --bootnodes /ip4/13.39.104.56/tcp/30333/p2p/12D3KooWJmNgQE6hftytjeXnwNRNrkxFLoChSa5FSuU7F4DnBUEZ --validator --name mainnet-node01 --base-path /tmp/cherry-mainnet-node01 --rpc-methods=unsafe --rpc-cors all --rpc-external --ws external
	```

#### 2. Testnet

Methods:

1. Binary

	```bash
	./target/release/cherry --chain cherry-testnet \
	--name "<insert a name of your choice for you validator>" \
	--bootnodes /ip4/13.39.82.222/tcp/30333/p2p/12D3KooWChBa8Kk37fZuJJSqkkbYSzstXYXENnanCqDB5eMfA34A \
	--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
	--validator \
	--rpc-methods=unsafe \
	--rpc-cors all \
	--rpc-external \
	--ws external
	```

2. Docker

	```bash
	docker run --rm -it -p 9944:9944 -p 9933:9933 -p 30333:30333 -v $(pwd):/tmp/cherry-node cherrylabsorg/cherry-polkadot-node:dev --chain cherry-testnet --bootnodes /ip4/13.39.82.222/tcp/30333/p2p/12D3KooWChBa8Kk37fZuJJSqkkbYSzstXYXENnanCqDB5eMfA34A --validator --name testnet-node01 --base-path /tmp/cherry-testnet-node01 --rpc-methods=unsafe --rpc-cors all --rpc-external --ws external
	```

## Generating the Session Keys

You need to tell the chain your Session keys by signing and submitting an extrinsic. This is what associates your validator node with your Controller account on Cherry.

Since you’re using a remote server, it is easier to run this command on the same machine (while the node is running):

```bash
curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "author_rotateKeys", "params":[]}' http://localhost:9933
```

The output will have a hex-encoded “result” field. The result is the concatenation of the four public keys. Save this result for a later step.

You can restart your node at this point. Simply be pressing Ctrl-C(or docker restart <CONTAINER ID> if running via docker) and type the same command from [Running the `cherry` binary](../../quickstart/installing-the-cherry-node.md) section.

## Setup Validator Accounts

Open [https://cherry.place/#/explorer](https://cherry.place/#/explorer) in your browser

Navigate to `Accounts → Add Account` and create two accounts, one for your **Controller** and one for your **Stash.**

![](<../../.gitbook/assets/image (12).png>)

![](<../../.gitbook/assets/image (8) (1).png>)

![](<../../.gitbook/assets/image (18) (1).png>)

## Setup Validators

Navigate to **Network** → **Staking** → **Account Actions** → **+Validator**

![](<../../.gitbook/assets/image (14) (1).png>)

Select your **Stash** & **Controller**

![](<../../.gitbook/assets/Screenshot 2022-11-17 at 8.33.14 PM.png>)

Add your keys from the [**Generating the Session Keys**](become-a-validator.md#generating-the-session-keys) in the `Keys from rotateKeys` field

![](<../../.gitbook/assets/image (2) (1).png>)

Finally select **Bond & Validate**
