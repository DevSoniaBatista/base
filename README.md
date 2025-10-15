# Smart Contract Deployed
https://sepolia.basescan.org/address/0x32c62C09CF0C6eBDBa31f370A8c7B578b74746E0

# Project Overview
Simple Ethereum smart contract project using Foundry.  
Implements a `Greeting` contract with a mutable `string` message.  
Built following the instructions of the first Dev3pack challenge.

## Tech Stack
- Solidity ^0.8.13
- Foundry (Forge, Cast, Anvil)
- Base Sepolia network for deployment and verification

## Key Files
- `src/Greeting.sol`: Contract with `constructor(string)`, `setGreeting(string)`, and `greet()` methods.
- `test/`: Placeholder for unit tests.
- `lib/forge-std`: Foundry standard library submodule.
- `.env.example`: Sample environment variables for RPC and keys.

## Usage
Build:
```bash
forge build
```

Test:
```bash
forge test
```

## Deploy (Base Sepolia)
PowerShell example:
```bash
forge create src/Greeting.sol:Greeting --rpc-url $env:BASE_SEPOLIA_RPC_URL --broadcast --private-key $env:PRIVATE_KEY --constructor-args "Hello Base Builders-Brazil Sonia"
```

## Verify (Base Sepolia)
Encode constructor args:
```bash
cast abi-encode "constructor(string)" "Hello Base Builders-Brazil Sonia"
```

Verify:
```bash
forge verify-contract --chain base-sepolia --verifier etherscan --etherscan-api-key $env:BASESCAN_API_KEY --constructor-args <ENCODED_ARGS> <DEPLOYED_ADDRESS> src/Greeting.sol:Greeting
```

## Notes
- On PowerShell, reference environment variables with `$env:VAR`.
- If verification needs a direct endpoint, add `--verifier-url https://api-sepolia.basescan.org/api`.
- After cloning, run `git submodule update --init --recursive` to fetch `forge-std`.
