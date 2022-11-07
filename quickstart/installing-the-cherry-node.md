# Installing the Cherry Node

## Prerequisites

### Hardware Requirements

We suggest running the node on at least&#x20;

* RAM: 4GB
* CPU: 2
* Hard Disk Space: 40GB

Operating system: preferably a recent Debian-based Linux distribution.&#x20;

### Install Rust

For debian-based distros:

`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

> After installation, run `rustc --version` to check if the installation was successful.

### Install dependencies

For debian-based distros:

```shell
sudo apt update
sudo apt install -y git clang curl libssl-dev llvm libudev-dev pkg-config
```

{% hint style="info" %}
For other Linux Distribution please visit **Substrate's** Documentation [https://docs.substrate.io/v3/getting-started/installation/#1-build-dependencies](https://docs.substrate.io/v3/getting-started/installation/#1-build-dependencies). Keep in mind that we also need `pkg-config`installed.
{% endhint %}

### Initialize your wasm build environment

```shell
rustup update nightly
rustup update stable
rustup target add wasm32-unknown-unknown --toolchain nightly
```



## Running the Node

### Clone Cherry-Node repository

```bash
git clone https://github.com/CherryNetwork/Cherry-Node.git
cd Cherry-Node
```

### Run Build Script

#### Mainnet:

```bash
chmod +x scripts/run_mainnet.sh
./scripts/run_mainnet.sh
```

#### Testnet:

```bash
chmod +x scripts/run_testnet.sh
./scripts/run_testnet.sh
```

or you run it yourself if you installed all the required dependencies:

#### Mainnet:

```shell
cargo b --release && ./target/release/cherry 
--chain cherry-mainnet
--bootnodes /ip4/15.236.154.200/tcp/30333/p2p/12D3KooWC3UYsfPTpBvDr5oqc8CRe2jftT5kaVYpfhYojjLT4HWB 
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" 
```

#### Testnet:

```shell
cargo b --release && ./target/release/cherry 
--chain cherry-testnet 
--bootnodes /ip4/13.38.120.202/tcp/30333/p2p/12D3KooWBBz9C5t8vZBCPW1bhKwDDp2gqgMpSYTdWkZ2iBTLPxLd 
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0"
```
