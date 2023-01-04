# Installing the Cherry Node

## Prerequisites

### Hardware Requirements

We suggest running the node on at least

* RAM: 4GB
* CPU: 2
* Hard Disk Space: 40GB

Operating system: preferably a recent Debian-based Linux distribution.

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

1.  Clone cherry-relay-node repository

    ```bash
    git clone https://github.com/CherryNetwork/cherry-relay-node.git
    cd cherry
    ```

2.  Run Cherry Binary
    
    * Mainnet

        1. Script

            ```bash
            chmod +x scripts/run_mainnet.sh
            ./scripts/run_mainnet.sh
            ```

        2. Binary

            ```shell
            cargo b --release && ./target/release/cherry \ 
                --chain node/service/chain-specs/mainnet-relay-regenesis.json \
                --bootnodes /ip4/15.236.154.200/tcp/30333/p2p/12D3KooWQTgHfboF9q1Ni8q3vG3MVJL5RMxYxYJvLnw3z7P2Mejp \ 
                --telemetry-url "wss://telemetry.polkadot.io/submit/ 0"
            ```
        
        3. Docker

            ```bash
            docker run --rm -it -p 9944:9944 -p 9933:9933 -p 30333:30333 \ 
	        -v $(pwd):/tmp/cherry-node -d cherrylabsorg/cherry-node:latest cherry \
	        --chain node/service/chain-specs/mainnet-relay-regenesis.json --bootnodes /ip4/15.236.154.200/tcp/30333/p2p/12D3KooWQTgHfboF9q1Ni8q3vG3MVJL5RMxYxYJvLnw3z7P2Mejp
            ```
            


    * Testnet

        1. Script

            ```bash
            chmod +x scripts/run_testnet.sh
            ./scripts/run_testnet.sh
            ```

        2. Binary

            ```shell
            cargo b --release && ./target/release/cherry \ 
               --chain cherry-testnet \
                --bootnodes /ip4/13.39.49.17/tcp/30333/p2p/12D3KooWRx5Uv8V3AcKiDHc1eKKhFBenmg7rJHnrFTpaiCtUomX9 \
                --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" 
            ```

        3. Docker

            ```bash
            docker run --rm -it -p 9944:9944 -p 9933:9933 -p 30333:30333 \ 
	        -v $(pwd):/tmp/cherry-node -d cherrylabsorg/cherry-node:latest cherry \
	        --chain cherry-testnet \
            --bootnodes /ip4/13.39.49.17/tcp/30333/p2p/12D3KooWRx5Uv8V3AcKiDHc1eKKhFBenmg7rJHnrFTpaiCtUomX9
            ```
