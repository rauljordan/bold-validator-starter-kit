# Arbitrum BOLD Validator Starter Kit

This repository contains two docker compose setups for validators in Arbitrum BOLD. Both an honest and evil validator can participate in BOLD challenges on Ethereum sepolia.

## Running

You can choose to run either an honest or an evil validator on Ethereum sepolia. Note that your validator must have a special testnet Weth ERC20 token to participate in challenges and must have approved the rollup and challenge manager contracts to spend it. To do so, you can use a special tool found [here](https://github.com/OffchainLabs/bold/blob/main/tools/fund-weth/main.go) or contact us to seed you with some of this test Weth funds.

You will also **need an Ethereum Sepolia RPC connection**. We recommend [Infura](https://infura.io) as an option or running your own Sepolia testnet node.

## Honest Validator

To run an honest validator, modify these values inside of `honest-validator/validator_config.json`

on line 2:

```json
    "parent-chain": {
        "connection": {
            "url": "" // ADD YOUR L1 Sepolia HTTP Endpoint here
        },
        "wallet": {
            "private-key": "" // ADD YOUR VALIDATOR PRIVATE KEY STRING HERE
        }
    },
```

## Evil Validator

To run an evil validator, modify these values inside of `evil-validator/evil_validator_config.json`

on line 2:

```json
    "parent-chain": {
        "connection": {
            "url": "" // ADD YOUR L1 Sepolia HTTP Endpoint here
        },
        "wallet": {
            "private-key": "" // ADD YOUR VALIDATOR PRIVATE KEY STRING HERE
        }
    },
```

### How Evil Validators Work

Evil validators at the moment intercept all Arbitrum deposit transactions to the inbox that have a value of 1M gwei, or 0.001 ETH. To modify the amount to intercept, change **all instances** of `evil-intercept-deposit-gwei` in your `evil-validator/evil_validator_config.json` to a different amount of gwei.