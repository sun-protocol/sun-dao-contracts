## sun-dao-contracts

This repository contains the core Vyper smart contracts used by the **Sun Governance DAO**.  
These contracts implement vote-escrowed tokens, liquidity gauges, reward distribution, and related governance logic.

The goal of this codebase is to provide a transparent and extensible on-chain governance and incentive system for the Sun ecosystem.

---

## Overview

- **Language**: Vyper  
- **Domain**: Governance, staking, and reward distribution for the Sun DAO  
- **Key concepts**:
  - **Vote-escrowed token (`veSUN`)** for governance and long-term alignment
  - **Gauge system** for directing rewards to different pools
  - **Minter and distribution contracts** for emission and reward distribution

All contracts are designed to be deployed on-chain and interacted with by governance, users, and other protocol components.

---

## Contracts

Below is a high-level description of the main contracts in this repository.  
The original intent and semantics are preserved, with clearer wording in English.

- **`veSUN`**:  
  Vote-escrowed SUN token for the Sun DAO, acting as an equity-like certificate for governance.  
  Users lock SUN for a period of time to receive `veSUN`, which is typically used for:
  - Participating in DAO governance and voting
  - Directing emissions or rewards via gauges

- **`Gauge`**:  
  Farming (staking) pool for depositing SUN or other supported assets.  
  Gauges:
  - Track user stakes
  - Accrue rewards emitted by the protocol
  - Are usually weighted by `veSUN` votes via the gauge controller

- **`GaugeController`**:  
  Controller contract that manages gauges and their relative weights.  
  It:
  - Registers and tracks all gauges
  - Stores voting weights and parameters
  - Determines how rewards are allocated across gauges based on governance decisions

- **`minter`**:  
  Reward minting contract that mints or releases rewards, sourcing them from the `Distribution` contract.  
  It:
  - Acts as the authorized minter for reward tokens
  - Interfaces with gauges and/or other contracts to distribute emissions

- **`Distribution`**:  
  Reward distribution contract that holds reward assets.  
  Only the `minter` contract is allowed to transfer assets from this contract, ensuring:
  - Centralized control of emissions logic in `minter`
  - Separation of concerns between asset storage and minting logic

---

## Deployments

The following table lists the known deployment addresses of the contracts.

| Contract | Address |
|:--------|:--------|
| `veSUN` | TXcsJpLqjDCf6fJkHfUqGNHFRPzxVQNjpy |

> Note: This table may not be exhaustive. Always verify deployment addresses from official Sun DAO channels before interacting on-chain.

---

## Development

### Prerequisites

- Python and Vyper toolchain installed
- A supported network RPC endpoint (for deployment and testing)

### Basic workflow

1. **Install dependencies** (if this repository defines any tooling or environment):  
   Set up your Python/Vyper environment according to your local standards.
2. **Compile contracts**:  
   Use Vyper to compile the contract sources in this repository.
3. **Deploy contracts**:  
   Deploy using your preferred deployment framework or scripts, passing in the correct constructor parameters and governance addresses.
4. **Run tests** (if present):  
   Execute any test suite to validate contract behaviour before mainnet or production deployment.

> Implementation details (such as exact commands and scripts) depend on your local environment and tooling and can be added here as the repository evolves.

---

## Security and Audits

Smart contracts in this repository are intended to secure real assets and protocol governance.  
Before deploying to production or interacting with large amounts of value:

- Ensure contracts have undergone **thorough internal review and external audits**.
- Carefully review any upgrades or configuration changes via DAO governance.
- Follow best practices for key management and admin / governance permissions.

If you discover a potential vulnerability, please reach out via the community channels below.

---

## Community

If you have any questions about this project, or wish to engage with us:

- Telegram: [`https://t.me/SunIO_Defi`](https://t.me/SunIO_Defi)
- Twitter: [`https://twitter.com/defi_sunio`](https://twitter.com/defi_sunio)

Official channels are the best place to get updated information about deployments, governance proposals, and releases.
