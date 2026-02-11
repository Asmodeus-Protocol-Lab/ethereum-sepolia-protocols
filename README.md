# Ethereum Sepolia – Protocol Experiments

This repository contains protocol-level experiments built on **Ethereum Sepolia**.
The goal is to explore core EVM design patterns, long-lived state management,
and governance mechanics under Ethereum’s security and execution assumptions.

This is a **research and implementation lab**, not a production application.

---

## Projects

### 1. ForgeToken
A governance-enabled ERC-20 implementation with capped supply and delayed
administrative controls.

**Focus areas**
- Access control patterns
- Supply discipline
- Upgrade-safe storage layout
- Ethereum security assumptions

---

### 2. StakeWeave
An epoch-based staking and reward distribution system with extensible slashing hooks.

**Focus areas**
- Long-lived on-chain state
- Reward calculation safety
- Epoch management
- Slashing and penalty modeling

---

### 3. OnChainCouncil
A minimal on-chain governance system supporting proposals, voting, quorum,
and delayed execution.

**Focus areas**
- Governance primitives
- Voting mechanics
- Quorum and execution rules
- Timelock-style controls

---

## What This Repository Demonstrates

- Solidity best practices
- Gas-conscious contract design
- Secure state transitions
- Ethereum-native governance patterns

---

## Network

- **Chain:** Ethereum
- **Testnet:** Sepolia

---

## Deployments

> Deployment details will be added as contracts are finalized and deployed.

- ForgeToken: _pending_
- StakeWeave: _pending_
- OnChainCouncil: _pending_

---

## Notes

Each project is intentionally scoped and isolated to focus on specific protocol
design concerns. No frontend is included by design.
