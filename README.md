# Pinbook

Pinbook is a high-performance, zero-copy on-chain order book engine for Solana.

The project focuses on building an efficient order book implementation using Rust and Pinocchio, with an emphasis on deterministic memory usage, minimal computation, and allocator-free execution.

Pinbook is designed to support execution through MagicBlock Ephemeral Rollups for latency-sensitive order book operations, while using Solana as the canonical settlement layer.

## Features

* Zero-copy account access
* Allocator-free execution
* Fixed-memory data structures
* Offset-based order references
* Price-time priority matching
* Limit and market orders
* Partial order fills
* Order cancellation and modification
* On-chain settlement
* MagicBlock Ephemeral Rollup support
* Optional oracle integration for reference pricing and risk management

## Architecture

Pinbook is divided into three core components:

### Data Structure

The order book stores bids, asks, price levels, and orders directly in account memory.

The implementation avoids unnecessary serialization, deserialization, copying, and heap allocation.

### Matching Engine

The matching engine implements price-time priority and handles:

* Limit orders
* Market orders
* Partial fills
* Order cancellation
* Order modification
* Best bid and ask discovery

### Settlement

After orders are matched, the settlement layer updates user balances and handles locked funds, token transfers, and protocol fees.

## MagicBlock

Pinbook is designed to use MagicBlock Ephemeral Rollups for high-frequency order book execution.

The order book can be delegated to an Ephemeral Rollup for low-latency execution, with finalized state ultimately settled on Solana.

## Oracle

Oracle data is not part of the core matching path.

Oracle integration can be used for reference pricing, risk management, liquidation mechanisms, and other market-safety requirements.

## Goals

The primary goal of Pinbook is to explore how efficiently an on-chain order book can be implemented when account memory is treated as the underlying data structure.

The project prioritizes:

* Memory efficiency
* Compute efficiency
* Deterministic execution
* Minimal data movement
* Low-latency order matching
* Safe and atomic settlement

## Status

Pinbook is currently under active development and should be considered experimental.

## License

TBD — see [LICENSE](LICENSE)
