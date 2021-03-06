# SubDEX chain

A DEX built on [Substrate Note Template](https://github.com/substrate-developer-hub/substrate-node-template) :rocket:

### Simple Method

You can install all the required dependencies with a single command (be patient, this can take up
to 30 minutes).

```bash
curl https://getsubstrate.io -sSf | bash -s -- --fast
```

### Manual Method

Manual steps for Linux-based systems can be found below:

Install Rust:

```bash
curl https://sh.rustup.rs -sSf | sh
```

Initialize your Wasm Build environment:

```bash
./scripts/init.sh
```

### Build

Once you have prepared your local development environment, you can build the DEX. Use this
command to build the [Wasm](https://substrate.dev/docs/en/knowledgebase/advanced/executor#wasm-execution)
and [native](https://substrate.dev/docs/en/knowledgebase/advanced/executor#native-execution) code:

```bash
cargo build --release
```

## Run

### Single Node Development Chain

Purge any existing developer chain state:

```bash
./target/release/subdex-node purge-chain --dev
```

Start a development chain with:

```bash
./target/release/subdex-node --dev
```

Detailed logs may be shown by running the node with the following environment variables set:
`RUST_LOG=debug RUST_BACKTRACE=1 cargo run -- --dev`.

### Multi-Node Local Testnet

If you want to see the multi-node consensus algorithm in action, refer to
[our Start a Private Network tutorial](https://substrate.dev/docs/en/tutorials/start-a-private-network/).

### Run in Docker

First, install [Docker](https://docs.docker.com/get-docker/) and
[Docker Compose](https://docs.docker.com/compose/install/).

Then run the following command to start a single node development chain.

```bash
./scripts/docker_run.sh
```

This command will firstly compile your code, and then start a local development network. You can
also replace the default command (`cargo build --release && ./target/release/subdex-node --dev --ws-external`)
by appending your own. A few useful ones are as follow.

```bash
# Run Substrate node without re-compiling
./scripts/docker_run.sh ./target/release/subdex-node --dev --ws-external

# Purge the local dev chain
./scripts/docker_run.sh ./target/release/subdex-node purge-chain --dev

# Check whether the code is compilable
./scripts/docker_run.sh cargo check
```
