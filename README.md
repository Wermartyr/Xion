# Xion

### 1. Environment Setup
Ensure you have the following tools installed:
- **Go 1.21**: Required for building the Xion Daemon. You can install Go by following the official [Go installation guide](https://go.dev/doc/install).
- **Git**: Needed for cloning the repository.

### 2. Build the Xion Daemon
First, clone the Xion repository and build the `xiond` binary:
```bash
git clone https://github.com/burnt-labs/xion.git
cd xion
make install
```
This will install the binary to your `$PATH`.

### 3. Configuration Setup
After installing `xiond`, configure the following files:
- **app.toml**: For application-specific settings.
- **config.toml**: For consensus and network settings.
- **client.toml**: For client configurations.

These files can be found in the `~/.xion/config/` directory.

### 4. Join the Network
To join the Xion test network, use the following command:
```bash
xiond start --home ~/.xion
```

### 5. Create a Validator
Once your node is synchronized, you can create a validator:
1. Create a wallet:
    ```bash
    xiond keys add <wallet_name>
    ```
2. Obtain test tokens via the faucet.
3. Create the validator:
    ```bash
    xiond tx staking create-validator \
    --amount=<amount> \
    --from=<wallet_name> \
    --pubkey=$(xiond tendermint show-validator) \
    --moniker="<moniker_name>" \
    --chain-id=xion-testnet-1 \
    --commission-rate="0.10" \
    --commission-max-rate="0.20" \
    --commission-max-change-rate="0.01" \
    --min-self-delegation="1"
    ```

After completing these steps, your validator will be added to the network and start participating in consensus.

