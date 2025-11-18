# Solana Raydium Pumpfun Token Sniper Bot

A high-performance token sniper bot for Solana, built in Rust, designed to detect and execute trades on newly launched tokens across Raydium and Pump.fun with minimal latency.

## Overview

This bot monitors new token launches in real-time using multiple gRPC connections to data providers (Helius, Yellowstone) and executes buy/sell orders with ultra-low latency through Jito block engines. Built with Rust for performance, memory safety, and reliability.

## Features

- **Low-Latency Execution**: Optimized for speed with Rust's performance characteristics
- **Multiple gRPC Connections**: Real-time monitoring via Helius and Yellowstone
- **Jito Integration**: Supports Jito, Nozomi, Zeroslot, and NextBlock for fast transaction confirmation
- **Multi-Wallet Support**: Bundle transactions across up to 20 wallets
- **DEX Support**: Raydium, Pump.fun, Meteora, and Orca

## Project Structure

```
src/
├── core/           # Token and transaction handling
├── engine/         # Swap logic and monitoring (Helius/Yellowstone gRPC)
├── dex/            # DEX implementations (Pump.fun, Raydium, Meteora, Orca)
├── services/       # Jito services (Jito, Nozomi, Zeroslot, NextBlock)
├── common/         # Utilities and logging
├── lib.rs
└── main.rs
```

## Configuration

Set the following environment variables:

```plaintext
PRIVATE_KEY=<your_wallet_private_key>
RPC_API_KEY=<helius_rpc_api_key>  # Premium version with Geyser Enhanced Websocket required
SLIPPAGE=10
JITO_BLOCK_ENGINE_URL=https://ny.mainnet.block-engine.jito.wtf
JITO_TIP_VALUE=0.00927
TIME_EXCEED=60                     # Seconds; time limit for volume non-increasing
TOKEN_AMOUNT=0.0000001             # Token amount to purchase
TP=3                               # Take profit multiplier
SL=0.5                             # Stop loss percentage (50%)
```

## Usage

1. Configure environment variables as shown above
2. Add target wallet addresses to monitor (one per line)
3. Run the executable: `solana-pumpray-sniper.exe`

### Strategy

- **Entry**: Execute buy order when monitored wallets purchase new tokens
- **Exit**: Execute sell order based on TP/SL conditions or time limit
- **Time Limit**: Auto-sell positions open longer than 60 seconds (configurable)

## Trial Version

A trial version is available for testing. The strategy follows the entry/exit triggers described above with configurable TP/SL and time limits.

**Test Results**: Successfully executes trades in the same block as detection.

## Requirements

- Dedicated server located in New York recommended for optimal performance
- Premium Helius RPC API key with Geyser Enhanced Websocket

## Support

For inquiries and support, contact via Telegram: [Alberto](https://t.me/ferris)

## Donations

6vT7nrqtbXDWVc8cRUtifxgfDZi19aW7qhcZg2hSepwb
