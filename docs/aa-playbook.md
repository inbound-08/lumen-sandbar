docs/aa-playbook.md# Lumen Sandbar — Account Abstraction (AA) Playbook

This document maps **Base account abstraction concepts** to concrete validation steps
used during development and review.

---

## Core Concepts

### Base Account Abstraction
Base supports smart accounts that abstract:
- EOA vs contract wallet differences
- Gas sponsorship / paymasters
- Batched and sponsored transactions

In Lumen Sandbar, AA concepts are treated as **capabilities to validate**, not assumptions.

---

## Practical Validation Steps

### 1) Account Creation
- Ensure smart account creation logic is deterministic
- Validate that account addresses are stable across reloads
- Confirm no implicit dependency on EOAs

Reference conceptually:
- `createBaseAccount` (used as a mental model / API reference)
- Account factory + initCode patterns

Checklist:
- [ ] Account address resolves before first transaction
- [ ] No funds required for initial read-only calls
- [ ] Creation works on Base Sepolia before Mainnet

---

### 2) Read-only Safety
Smart accounts must support:
- Balance reads
- Token metadata reads
- Allowance checks

Validation:
- [ ] Read calls succeed without gas sponsorship
- [ ] RPC fallback works for account reads

---

### 3) Transaction Simulation
Before submitting:
- Simulate execution against Base RPC
- Confirm revert reasons are surfaced

Checklist:
- [ ] Simulation matches on-chain behavior
- [ ] No hidden assumptions about msg.sender

---

## Notes

- Treat AA features as **opt-in**
- Avoid hard dependencies on a single account implementation
- Always validate on **Base Sepolia first**

_Last updated: initial scaffold_
