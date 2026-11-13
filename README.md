leash/
├── README.md
├── contracts/
│   └── leash/
│       └── src/
│           └── lib.rs
├── frontend/
│   └── index.html
└── scripts/
    └── demo.js
# Leash

On-chain spending limits for AI agents on NEAR.

## Problem

Giving an AI agent a full-access key is dangerous. Prompt injection, bugs, or a compromised model can drain the entire wallet in one transaction.

## Solution

Leash uses NEAR’s native function-call access keys + an on-chain policy vault.

- The agent only receives a **function-call key**.
- That key can call only one method: `spend`.
- The vault contract checks every payment against the owner’s policy before any funds move.
- The owner can pause the agent or change the policy at any time.

## Policy enforced on-chain

- Maximum amount per payment
- Daily spending budget
- Receiver allowlist
- Optional human approval above a threshold
- Instant pause by owner

## How it works

1. Owner deploys/funds the vault and sets the policy.
2. Owner adds a function-call key for the agent (restricted to the vault contract and the `spend` method).
3. Agent can only call `spend`. The protocol itself rejects any attempt to transfer, add keys, or call other contracts.
4. The vault contract applies the policy on every call.

## Tracks

- AI Security & Defense
- Agent Economy

## Built for NEAR HACKATHON 2026

@NEARProtocol #NEARHackathon
