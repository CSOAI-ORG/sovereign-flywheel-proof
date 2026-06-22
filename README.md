# Sovereign Town — Governed-vs-Ungoverned Flywheel Proof (CSOAI / MEOK)

A headless simulation runs two arms over an ever-advancing seed window: **A = governed** AI agents,
**B = ungoverned**. Each cycle appends an **Ed25519-signed, hash-chained** summary to this ledger.
**You do not have to trust CSOAI** — verify it yourself with the public key.

## Headline (recomputed from this ledger)
```
cycles=515 episodes=654091200 governed_crimes=0 ungoverned_crimes=54714864
```
**Read this honestly:** the governed arm shows 0 because this ledger ran the Sovereign Gate at
**perfect enforcement (block_rate=1.0)** — it blocks 100% of *attempted* crimes, so 0 is true *by
construction*, NOT emergent crimelessness. The real, defensible finding is the **dose-response**:
on identical agents/seed, violations fall **647 → 210 → 0** as enforcement rises **0% → 50% → 100%**
(ungoverned control ≈ 645). Governance works *proportionally to enforcement*. These are **rule-based
agent-based-model agents, not LLMs**, and this is an **in-simulation** result.

## Verify it yourself
```
pip install cryptography
python3 verify_flywheel.py flywheel_ledger.jsonl town_pub.key
```
It recomputes each cycle's signed message, checks the Ed25519 signature against `town_pub.key`,
and validates the hash-chain.

## Honest notes (the audit found these — we don't hide them)
- **Cycles 1–30 predate a key rotation** and do not verify against the current `town_pub.key`;
  the **hash-chain is intact end-to-end** (no tampering — a key-continuity gap). Cycles from ~31
  onward verify. The prior key was not preserved; key persistence is being fixed.
- This is an **in-simulation** result (synthetic agents/episodes), not a real-world claim.
- The signature proves the cycle summary was signed by the holder of `town_pub.key` and not
  altered since — it does not by itself prove the simulator's internal correctness.
