# Solana Token Presale Platform

A comprehensive Solana-based token presale smart contract system built with the Anchor framework. This project provides a complete foundation for managing token presales on the Solana blockchain with advanced features and robust security.

## Core Features

### Presale Management
- Multi-stage presale system with 10 configurable stages
- Flexible pricing strategies per stage
- Automated stage progression based on token sales
- Admin-controlled stage management

### Payment Options
- SOL payments with real-time price conversion
- Stable coin support (USDC/USDT)
- Pyth price feed integration for accurate SOL/USD pricing
- Automatic token allocation calculations

### Security & Administration
- Comprehensive admin controls for presale management
- User state tracking for purchase history
- Secure token transfer mechanisms
- Robust error handling and input validation

## Technical Stack

- **Framework**: Anchor
- **Blockchain**: Solana
- **Language**: Rust
- **Testing**: TypeScript with Anchor tests
- **Price Feeds**: Pyth Network

## Quick Start Guide

### Prerequisites

Ensure you have the following installed:
- Node.js and Yarn
- Rust programming language
- Solana CLI tools
- Anchor framework

### Installation

```bash
git clone https://github.com/blixor7/Solana-Token-Presale-Platform.git
cd token-presale-smart-contract
yarn install
```

### Build and Deploy

1. **Build the program**:
   ```bash
   anchor build
   ```

2. **Get program address**:
   ```bash
   solana-keygen pubkey ./target/deploy/presale-keypair.json
   ```

3. **Update program ID**:
   - Replace the program ID in `programs/presale/src/lib.rs`
   - Update `Anchor.toml` with your program address

4. **Deploy to network**:
   ```bash
   anchor deploy
   ```

## Configuration

### Network Setup

Update `Anchor.toml` with your preferred network:

```toml
[provider]
cluster = "devnet"  # Options: localnet, devnet, testnet, mainnet-beta
wallet = "./admin.json"
```

### Presale Initialization

Use the CLI tools to set up your presale:

```bash
# Initialize project with token
yarn script init -t <TOKEN_ADDRESS>

# Set DAO wallet for funds
yarn script set-vault -v <DAO_WALLET_ADDRESS>

# Deposit tokens to presale
yarn script deposit-token -t <TOKEN_ADDRESS> -a <DEPOSIT_AMOUNT>

# Start presale
yarn script start-presale -t <TOKEN_ADDRESS>
```

## Testing

Run the comprehensive test suite:

```bash
anchor test
```

The test suite covers:
- Contract initialization
- User state management
- Token purchase functionality
- Stage management
- Admin controls
- Error conditions

## Smart Contract Architecture

### Key Components

- **Global State**: Manages presale configuration and admin settings
- **User State**: Tracks individual purchase history and allocations
- **Stage Management**: Handles multi-stage presale logic
- **Price Integration**: Real-time price feeds for accurate conversions

### Security Features

- Admin-only function access control
- Input validation and bounds checking
- Secure token transfer mechanisms
- Comprehensive error handling
- Price feed staleness checks

## Recent Improvements

### Security Enhancements
- Removed unsafe `unwrap()` calls
- Added stale price feed detection
- Improved stage validation logic
- Enhanced error handling throughout

### Code Quality
- Better error messages for debugging
- Consistent stage management
- Improved validation functions
- Robust state management helpers

## CLI Commands Reference

```bash
# Initialize presale
yarn script init -t <TOKEN_ADDRESS>

# Set vault address
yarn script set-vault -v <DAO_WALLET_ADDRESS>

# Deposit tokens
yarn script deposit-token -t <TOKEN_ADDRESS> -a <AMOUNT>

# Start presale
yarn script start-presale -t <TOKEN_ADDRESS>

# Set stage
yarn script set-stage -s <STAGE_NUMBER>
```

## Error Handling

The contract includes comprehensive error handling for:
- Invalid stage transitions
- Stale price feeds
- Insufficient funds
- Presale state violations
- Admin access control

## License

This project is licensed under the MIT License.

---
