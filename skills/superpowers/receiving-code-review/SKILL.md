---
name: receiving-code-review
description: Use when a Writer or Repair Writer receives a code-review finding batch; verifies the feedback against the accepted contract and codebase before making the smallest causally complete correction.
---

# Receiving Code Review

## Story实施、审查与修复边界

1. **首次Writer完整实现批准的Story**，把范围内的行为和接线做完整。
2. **首次Reviewer独立完整审查；后续Reviewer只检查当前批准的修复及其明确影响。** 原来通过的审查结论和测试结果按原范围保留，不自动失效、不重复审查或重跑。
3. **Repair Writer严格按批准内容修改。** 指定的问题、路径和验证范围就是边界；需要改别处或增加验证，先说明并取得批准，不能借“完整原因链”自行越界。

首次完整检查应覆盖批准范围内的实际行为和必要直接接线；后续Review只完成当前批准修复及明确影响的审查，继承原范围内已通过的结论和测试。完整提示词、完整报告和fresh Reviewer均不表示重审整个Story或重跑旧测试。

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

- Do not present guesses as facts, conceal uncertainty, or implement feedback merely because a Reviewer asserted it. Rely on explicit user decisions and applicable type, database, contract, and framework guarantees. An unsupported scenario alone is not a Repair requirement or blocker; discuss actual unresolved choices before dependent work.
- Make the smallest complete correction for verified findings, including necessary direct callers, data handling, and UI wiring within the approved scope; clean up only problems introduced by the current Repair.
- Do not add speculative behavior or failure flows based only on an error channel or an unsupported scenario; do not turn an unknown into a claim of impossibility.
- Place checks where data is accepted or a rule is enforced, including required business-state checks. Do not repeat a check downstream while the established guarantee remains valid.
- Reuse accepted error handling, preserve the original cause, and perform required cleanup. Never disguise failure as success, an empty result, or a default. Catch breadth alone does not determine correctness; explicit failure does not require crashing the whole application.
- A function or module may serve a concrete current responsibility even with one caller. Do not add interfaces, wrappers, factories, managers, or configuration only for hypothetical reuse; any scope change still requires approval.
- Define success criteria before editing and use only approved validation. Explain actual failures; do not repeat unchanged runs, change inputs, weaken assertions, or extend waits merely to obtain a pass.
