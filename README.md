# 🏦 Blueshift Anchor Vault

This is a simple Solana smart contract built with Anchor that allows users to securely **deposit** and **withdraw** SOL (lamports) to and from a **vault account** derived from their wallet address.

---

## 📦 Features

- One-time vault creation using program-derived addresses (PDAs)
- Deposit lamports into the user's vault
- Withdraw lamports back to the user's wallet
- Input validation for vault state and lamport amount

---

## 🔧 Instructions

### 📥 Deposit

Creates a new vault account (if it doesn't exist) and transfers the specified `amount` of lamports to it.

```ts
await program.methods
  .deposit(new anchor.BN(amount))
  .accounts({
    signer: user.publicKey,
    vault: vaultPda,
    systemProgram: anchor.web3.SystemProgram.programId,
  })
  .rpc();
