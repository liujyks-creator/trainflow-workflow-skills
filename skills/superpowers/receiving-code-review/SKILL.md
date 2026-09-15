---
name: receiving-code-review
description: Use when a Writer or Repair Writer receives a code-review finding batch; verifies the feedback against the accepted contract and codebase before making the smallest causally complete correction.
---

# Receiving Code Review

## Purpose

Turn one complete accepted finding batch into a technically verified Repair without blind agreement, partial understanding, or scope expansion.

## Lifecycle and transitions

```text
BATCH_BOUND -> FINDINGS_VERIFIED -> SUCCESS_DEFINED -> REPAIR_EXECUTED
-> VERIFIED -> RETURNED
```

- `BATCH_BOUND`: bind the complete accepted batch, reviewed candidate, authority, expected paths, hard-forbidden boundaries, causal-expansion rule, validation profile, and protected state.
- `FINDINGS_VERIFIED`: reproduce or source-prove every finding and identify shared causes without treating Reviewer wording as authority.
- `SUCCESS_DEFINED`: state the minimum causally complete production modification set and claim-to-evidence budget before editing.
- `REPAIR_EXECUTED`: use the accepted oracle and `../test-driven-development/SKILL.md` for behavior changes; route unexpected failures to `../systematic-debugging/SKILL.md`.
- `VERIFIED`: use `../verification-before-completion/SKILL.md` on the exact Repair candidate.
- `RETURNED`: return one complete terminal to management. Do not self-Review, merge, dispatch a Reviewer, or start another Story.

If the accepted oracle remains red, return to the supported root cause and the appropriate TDD/debugging state; do not weaken the oracle, pile on speculative changes, or repeat an unchanged gate until it happens to pass. Reach `RETURNED/DONE` only from `VERIFIED`. A missing authority or human-owned decision returns the precise blocked terminal instead of looping.

## Workflow

1. Read the complete batch before editing. Restate each requirement in technical terms and bind it to the accepted contract, exact candidate, affected path, and observable failure.
2. Verify every finding against the current codebase. If an item is unclear, conflicts with accepted authority, or requires a new product, architecture, ownership, data, or evidence decision, stop before editing and report the exact blocker.
3. Identify the shared root cause and adjacent direct consumers needed for a causally complete correction. Do not turn the scan into a general audit.
4. Use `../test-driven-development/SKILL.md` for approved behavior changes. Use `../systematic-debugging/SKILL.md` only for an observed unexpected or unexplained failure. Use `../verification-before-completion/SKILL.md` before any completion, commit, or push claim.
5. Close the accepted batch in one Repair candidate and report finding-to-change-to-evidence mapping. Do not self-Review, merge, or dispatch the next role.

Read-only investigation may inspect adjacent code, but a finding is not write authority outside the filled contract. An additional write path requires either an already accepted causal-expansion rule or an exact scope amendment before editing. If the complete Repair needs a new product, architecture, ownership, schema, migration, dependency, public-interface, security, or evidence decision, return `SCOPE_EXPANSION_REQUIRED` or the role contract's blocked terminal. Do not evade a closed boundary with a wrapper, adapter, fallback, duplicate authority, or partial fix.

Define the smallest sufficient evidence set before execution. Size it by demonstrated semantic risk propagation from the accepted contract, owner/consumer paths, public contracts, state, persistence, concurrency, packaging, real boundaries, or observed failures—not by change size or imagined possibility. Run focused and directly affected checks by default. Run a repository-wide suite only for an accepted gate, demonstrated repository-wide propagation, or proof that a narrower accepted suite cannot cover the claim. Rebuild artifacts or perform device/performance/external/human steps only when propagation reaches that boundary or the contract requires them. Do not repeat a passing unchanged gate. Stop when the complete accepted batch is closed, every claim has one fresh risk-matched proof, and all mandatory gates are satisfied.

## Repair Constraints

- Do not assume, conceal uncertainty, or implement feedback merely because a Reviewer asserted it. Expose decision-relevant uncertainty, load-bearing choices and trade-offs, their ripple effects, and the decision owner before editing depends on them.
- Change only what is necessary to solve the verified findings; clean up only problems introduced by the current Repair.
- Do not add speculative behavior, impossible-state guards, fallbacks, empty/default values, broad catches, silent recovery, or error swallowing.
- Trust accepted internal contracts and framework guarantees; validate only at real external or persistence boundaries.
- Preserve the original error signal and fail fast on invariant violations; never convert failure into rescue-nil behavior, a broad catch, a silent default, an empty success, or masked recovery.
- Do not create one-use helpers, tool classes, managers, registries, adapters, wrappers, or abstractions when a direct scoped change is sufficient.
- Define success criteria before editing and verify them with fresh, risk-matched evidence.
