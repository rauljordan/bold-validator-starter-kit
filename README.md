# Arbitrum BOLD Validator Starter Kit

This repository contains two docker compose setups for validators in Arbitrum BOLD. Both an honest and evil validator can participate in BOLD challenges on Ethereum sepolia.

## Running

You can choose to run either an honest or an evil validator on Ethereum sepolia. Note that your validator must have a special testnet Weth ERC20 token to participate in challenges and must have approved the rollup and challenge manager contracts to spend it.

You will also **need an Ethereum Sepolia RPC connection**. We recommend running your own Sepolia testnet node, as services such as infura run into rate limits.

## Installation Requirements

- Download 

## Honest Validator

First, fund your validator with the stake token needed on Sepolia:

```
./fund-stake-token.sh --private-key $HONEST_PRIV_KEY --eth-rpc-endpoint $SEPOLIA_ENDPOINT
```

```
./validator.sh --private-key $HONEST_PRIV_KEY --eth-rpc-endpoint $SEPOLIA_ENDPOINT
```

## Evil Validator

```
./validator.sh --evil --private-key $EVIL_PRIV_KEY --eth-rpc-endpoint $SEPOLIA_ENDPOINT
```

### How Evil Validators Work

Evil validators at the moment intercept all Arbitrum deposit transactions to the inbox that have a value of 1M gwei, or 0.001 ETH. To modify the amount to intercept, change **all instances** of `evil-intercept-deposit-gwei` in your `evil-validator/evil_validator_config.json` to a different amount of gwei.