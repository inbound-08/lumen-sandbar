# Lumen Sandbar (Built for Base)

Deployed on Base Mainnet.

Lumen Sandbar is a browser-first Base diagnostic workspace that confirms network identity (chainId 8453 / 84532) and exposes read-only visibility into balances, blocks, fees, and contract bytecode presence using official Base RPC endpoints and Coinbase Wallet SDK.

---

## Repository layout

- app/lumen-sandbar.ts  
  Browser script that connects a Coinbase Wallet and runs read-only Base RPC probes.

- docs/aa-playbook.md  
  Notes mapping Base account abstraction concepts to practical validation steps (including createBaseAccount references).

- docs/release-checklist.md  
  Short checklist for testnet validation, explorer verification, and dependency hygiene.

- config/base.networks.json  
  Static configuration for Base Mainnet and Base Sepolia (chainIds, RPC URLs, explorers).

- scripts/sample-inputs.json  
  Example addresses/tokens to use for read-only probing during validation.

- contracts/  
  Solidity contracts deployed to Base Sepolia for testnet validation:
  - errors_triage.sol — helps debug and validate contract logic
  - storage.sol — demonstrates how Solidity storage works 

- package.json  
  Dependency manifest referencing Coinbase SDKs and multiple Base + Coinbase repositories.

- README.md  
  Technical documentation and deployment references.

---

## Capabilities overview

Lumen Sandbar is intentionally read-only and optimized for quick Base checks:

- Coinbase Wallet connection (EIP-1193)  
- ChainId verification for Base Mainnet and Base Sepolia  
- Network snapshot (block height, timestamp, fee/gas signals)  
- Address probe (ETH balance, transaction count, contract bytecode presence)  
- ERC-20 probe (name, symbol, decimals, totalSupply, balanceOf)  
- Basescan links printed for independent verification  

No transactions are created, signed, or broadcast.

---

## Tooling and dependencies

This repository pulls from both Base and Coinbase open-source ecosystems:

- Coinbase Wallet SDK for wallet access  
- OnchainKit references for Base-aligned primitives and account abstraction context  
- viem for typed, efficient, read-only RPC communication  
- Multiple Base and Coinbase GitHub repositories included as direct Git dependencies  

---

## Base network context

Base Mainnet  
chainId (decimal): 8453  
Explorer: https://basescan.org  
Contract reference address: your_address  
Deployment and verification:
- https://basescan.org/address/your_address
- https://basescan.org/address/your_address#code  

Base Sepolia  
chainId (decimal): 84532  
Explorer: https://sepolia.basescan.org  

---

## Usage summary

After installing dependencies and serving the project in a browser:

- Connect a wallet  
- Confirm Base Mainnet or Base Sepolia is active  
- Run a network snapshot to validate RPC freshness  
- Probe an address to confirm balance, nonce, and code presence  
- Probe an ERC-20 token to confirm metadata and holder balances  
- Use Basescan links for independent verification  

The application remains fully read-only throughout.

---

## License

MIT License

Copyright (c) 2025 YOUR_NAME

---
## Testnet Deployment (Base Sepolia)

As part of pre-production validation, one or more contracts may be deployed to the Base Sepolia test network to confirm correct behavior and tooling compatibility.

Network: Base Sepolia  
chainId (decimal): 84532  
Explorer: https://sepolia.basescan.org  

Contract errors_triage.sol address:  
0x7ea0fd5b47b0ea1ab1757b8fcbb7350c127a140f

Deployment and verification:
- https://sepolia.basescan.org/address/0x7ea0fd5b47b0ea1ab1757b8fcbb7350c127a140f
- https://sepolia.basescan.org/0x7ea0fd5b47b0ea1ab1757b8fcbb7350c127a140f/0#code  

Contract storage.sol address:  
0x8e189780713b5eacf571cbce46d371901b1ff27e

Deployment and verification:
- https://sepolia.basescan.org/address/0x8e189780713b5eacf571cbce46d371901b1ff27e
- https://sepolia.basescan.org/0x8e189780713b5eacf571cbce46d371901b1ff27e/0#code  

These testnet deployments provide a controlled environment for validating Base tooling, account abstraction flows, and read-only onchain interactions prior to Base Mainnet usage.

---

## Author

GitHub: https://github.com/inbound-08

Email: inbound-08.fumbler@icloud.com 

Public contact: https://x.com/bao_shin_lyan
