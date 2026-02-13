# Ethereum Sepolia – Protocol Experiments

Production-grade protocol implementations on Ethereum Sepolia exploring governance, staking, and token mechanics at the base layer.

## Overview

This repository contains three protocol-level contracts demonstrating Ethereum-native design patterns:

1. **ForgeToken** - Governance-enabled ERC-20 with capped supply and timelock controls
2. **StakeWeave** - Epoch-based staking system with reward distribution and slashing
3. **OnChainCouncil** - Minimal on-chain governance with proposals, voting, and execution

Each contract implements security-first patterns, upgrade-safe storage layouts, and comprehensive testing infrastructure.

## Repository Structure

```
ethereum-sepolia-protocols/
├── contracts/
│   ├── ForgeToken/
│   │   └── ForgeToken.sol
│   ├── StakeWeave/
│   │   └── StakeWeave.sol
│   └── OnChainCouncil/
│       └── OnChainCouncil.sol
├── test/
│   └── foundry/
│       ├── ForgeToken/
│       │   ├── ForgeToken.t.sol
│       │   └── ForgeTokenInvariant.t.sol
│       ├── StakeWeave/
│       │   └── StakeWeave.t.sol
│       └── OnChainCouncil/
│           └── OnChainCouncil.t.sol
├── scripts/
│   └── deploy.ts
├── docs/
│   ├── specs/
│   │   ├── ForgeToken.md
│   │   ├── StakeWeave.md
│   │   └── OnChainCouncil.md
│   └── architecture/
│       └── system-design.md
├── deployment-records/
└── audits/
```

## Quick Start

### Prerequisites

- Node.js >= 18
- Foundry
- Git

### Installation

```bash
# Clone repository
git clone https://github.com/Asmodeus-Protocol-Lab/ethereum-sepolia-protocols.git
cd ethereum-sepolia-protocols

# Install dependencies
npm install

# Install Foundry dependencies
forge install OpenZeppelin/openzeppelin-contracts
```

### Configuration

```bash
# Copy environment template
cp .env.example .env

# Edit .env with your values
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR_KEY
PRIVATE_KEY=your_private_key
ETHERSCAN_API_KEY=your_etherscan_key
```

### Compile

```bash
# Hardhat
npm run compile

# Foundry
forge build
```

### Test

```bash
# Run all Foundry tests
forge test -vvv

# Run with gas reporting
forge test --gas-report

# Run coverage
forge coverage

# Run specific test file
forge test --match-path test/foundry/ForgeToken/ForgeToken.t.sol

# Run invariant tests
forge test --match-contract Invariant
```

### Deploy

```bash
# Deploy to Sepolia
npm run deploy:sepolia

# Verify contracts
npm run verify:sepolia
```

## Contract Addresses

### Sepolia Testnet

Deployments will be updated here after deployment.

| Contract | Address | Verified |
|----------|---------|----------|
| ForgeToken | `pending` | - |
| StakeWeave | `pending` | - |
| OnChainCouncil | `pending` | - |

## Documentation

### Technical Specifications

- [ForgeToken Specification](./docs/specs/ForgeToken.md)
- [StakeWeave Specification](./docs/specs/StakeWeave.md)
- [OnChainCouncil Specification](./docs/specs/OnChainCouncil.md)

### Architecture

- [System Design](./docs/architecture/system-design.md)

## Project Details

### ForgeToken

Governance-enabled ERC-20 implementation with:
- Capped supply (immutable hard cap)
- Role-based minting (MINTER_ROLE)
- Timelock-protected governance changes
- Comprehensive access control
- Upgrade-safe storage layout

**Use Cases**: Governance tokens, utility tokens with controlled issuance

### StakeWeave

Epoch-based staking contract with:
- 7-day epoch cycles
- Precise reward distribution using fixed-point math
- Slashing hooks for penalty enforcement
- Minimum stake duration (1 day)
- Multi-epoch reward accumulation

**Use Cases**: Token staking, validator bonding, reward distribution

### OnChainCouncil

Minimal governance system with:
- Proposal creation with threshold requirements
- Token-weighted voting
- Quorum validation (10% default)
- 2-day timelock before execution
- Arbitrary call execution capability

**Use Cases**: Protocol governance, DAO voting, parameter management

## Security

### Audit Status

Contracts are currently unaudited. This is a research and educational implementation.

**Do not use in production without professional security audit.**

### Security Features

- ReentrancyGuard on all state-changing external functions
- Custom errors for gas efficiency
- Timelock mechanisms on sensitive operations
- Role-based access control
- Comprehensive event emission

### Reporting Issues

If you discover a security vulnerability, please email: johnkenechukwu24@gmail.com (or create private security advisory on GitHub)

## Testing

Test coverage targets:
- Line coverage: >90%
- Branch coverage: >85%
- Function coverage: 100%

### Test Types

1. **Unit Tests**: Individual function behavior
2. **Integration Tests**: Multi-contract interactions
3. **Invariant Tests**: System-wide properties

### Running Tests

```bash
# All tests
forge test

# Specific contract
forge test --match-contract ForgeToken

# With verbosity
forge test -vvvv

# Gas snapshot
forge snapshot
```

## Gas Optimization

Implemented optimizations:
- Custom errors (saves ~50 gas per revert)
- Immutable variables where applicable
- Efficient storage packing
- Minimal storage writes

Estimated deployment costs (Sepolia):
- ForgeToken: ~1.2M gas
- StakeWeave: ~2.5M gas
- OnChainCouncil: ~3.1M gas

## Development Workflow

### Branch Strategy

```
main
├── develop
│   ├── feature/forge-token-v2
│   ├── feature/stakeweave-delegation
│   └── fix/council-quorum-calc
```

### Commit Convention

```
type(scope): description

[optional body]

[optional footer]
```

Types: `feat`, `fix`, `docs`, `test`, `refactor`, `chore`

### Pull Request Process

1. Create feature branch from `develop`
2. Implement changes with tests
3. Ensure all tests pass
4. Update documentation
5. Submit PR to `develop`
6. After review, merge to `develop`
7. Periodic releases merged to `main`

## Deployment Checklist

Before mainnet deployment:

- [ ] Complete security audit
- [ ] Verify all tests pass
- [ ] Review gas optimizations
- [ ] Confirm access control setup
- [ ] Test on Sepolia extensively
- [ ] Prepare multisig for admin roles
- [ ] Document emergency procedures
- [ ] Set up monitoring and alerts

## Contributing

This is an educational/research project. Contributions welcome for:
- Additional test coverage
- Gas optimizations
- Documentation improvements
- Bug fixes

## License

MIT

## Acknowledgments

Built on:
- OpenZeppelin Contracts
- Foundry
- Hardhat

Inspired by:
- Compound Governance
- Synthetix Staking
- Uniswap V3

## Contact

- GitHub: [@Asmodeus-Protocol-Lab](https://github.com/Asmodeus-Protocol-Lab)
- Project: Protocol Engineering Bootcamp

## Disclaimer

These contracts are experimental and educational. They have not been audited. Use at your own risk. The authors assume no liability for any losses incurred through use of this code.
