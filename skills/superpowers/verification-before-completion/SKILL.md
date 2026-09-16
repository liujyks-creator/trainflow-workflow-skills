---
name: verification-before-completion
description: Use before claiming a candidate is complete, fixed, passing, ready, or safe to commit or push; maps the exact claim to fresh, risk-matched evidence and reports any missing gate honestly.
---

# Verification Before Completion

## Purpose and Authority

Evidence must precede every completion, correctness, readiness, commit, or push claim. This skill defines a verification method; it does not grant scope, permission, integration authority, review authority, or permission to replace a human or device gate.

First apply user and system instructions, repository and role contracts, the immutable task or complete finding batch, and accepted product and code contracts. Fix the exact candidate identity, allowed scope, protected and unrelated state, accepted behavior and non-goals including excluded states, baseline failures or warnings, observable success and failure, and required evidence layers. Stop if a new authority or architecture decision is needed.

Verification does not authorize a fix. Candidate regressions return to the approved implementation scope; unrelated baseline issues remain evidenced and reported. Rely on explicit user decisions and applicable type, database, contract, and framework guarantees; label unsupported claims as unknown rather than inventing blockers. Check the complete current responsibility, including direct callers, data handling, and UI wiring. Validation belongs where a guarantee is established or a rule is enforced, with no duplicate downstream check while that guarantee remains valid. A function with one caller may serve a real current responsibility; neither call count nor catch breadth alone proves overengineering. Verify that accepted error handling preserves the cause and required cleanup without disguising failure as success, an empty result, or a default. Do not create speculative infrastructure or change inputs, assertions, waits, or retry behavior merely to make an oracle pass; stay within approved validation and explain actual failures.

## 用户流程与最小必要检查

以下规则约束本文件中的完整读取、身份核验、独立核对和交付检查，不新增审批层、报告文件、测试或检查轮次。
1. 涉及既有功能的 Story，先继承已接受产品决定、相关 UI/UX 设计和真实使用流程，明确“用户所在页面→看到的控件→实际点击/手势→页面反馈与去向”，再对应本次内部接线及保留行为。交接必须给出准确来源和必要章节；单条测试流程、源码调用链或接口状态不能代替整个 Story 的用户流程。只读相关片段，不为继承依据通读全部产品文档；已有决定直接沿用，真正冲突才讨论。
2. 疑问先说明具体用户操作链、当前影响及依据。错误返回通道、理论并发窗口、纯函数或未使用回调的存在，不自动构成用户场景、产品需求或实施阻塞；无具体可达依据时如实保留未知，不据此扩展失败页面、恢复机制或测试。实际正常操作出现接线缺陷应修正接线，不以失败提示替代修复；不吞错、不把未证实说成不可能。
3. 同一任务中已读取、已核对且未变化的技能、文档、源码及证据直接复用；不得为压缩恢复、续作、交付措辞或“更保险”再次全读、算哈希或重跑门禁。提示词模板适用下一条的每次必读例外。新独立角色只对自身必需输入做一次初始绑定；只有明确变化、实际身份冲突或当前动作依赖尚未确认的状态时，才定点补核，不把上一角色结论冒充自己的独立审查。
4. 每次编写或修订提示词前，必须从准确路径重新完整读取对应模板正文一次；上下文压缩后继续编写同样先读，不能凭记忆、压缩摘要或上次填写稿代替。此要求仅授权读取模板，不自动触发模板完整性审计、哈希核验、Git检查或其他来源重读。未修改原模板时，不重新审计其正文完整性。新生成提示词只对本次填写/修改内容及其必须保留的规则做一次必要检查；不能把原样保留模板变成全文反复比对任务。交接检查首先确认用户流程、已有决定、此次改动及直接消费者的对应关系；占位符清零、哈希一致和格式完整不能代替这项判断。
5. Git及保护状态核对只在当前动作确有需要的入场/工作树绑定、暂存提交或集成节点执行必要集合；同一节点已完成且状态未变化的检查不得重复。规划续作、普通答疑、文案整理不得自动触发整套Git、哈希或保护资产审计；不取消已批准且尚未完成的必要门禁。
6. 搜索先限定直接相关文件、章节和符号；长文档先定位再取片段，不用宽泛关键词跨大量历史全文输出。已有证据足够回答或完成当前修改立即停止；输出过宽时收窄，不追加更大调查。不得为证明自己检查过而创建额外清单、脚本、报告或测试。
7. 发生交接失误时，依据实际记录说明遗漏和影响；不能未经检查就宣称整段实现都在猜、全部无效或必须重开。保留已完成工作，只修正有依据的缺口。用户要求减少消耗时立即收窄或停止无必要操作，不能拿治理要求解释反复检查。

## Lifecycle and transitions

```text
CLAIM_BOUND -> EVIDENCE_SELECTED -> EVIDENCE_EXECUTED
-> PROVEN | NOT_PROVEN -> RETURN
```

- `CLAIM_BOUND`: identify the exact candidate, claim, direct risks, required gates, and protected state.
- `EVIDENCE_SELECTED`: map every direct risk to the smallest sufficient real oracle and define the stop condition before execution.
- `EVIDENCE_EXECUTED`: each selected oracle reaches terminal output against the bound candidate.
- `PROVEN`: every risk inside the claim has adequate fresh evidence and every mandatory gate passed.
- `NOT_PROVEN`: report the failing or missing oracle, evidence limit, and recovery condition without converting verification into implementation.
- `RETURN`: return the verified state to the current Writer, Reviewer, Repair, or management role. Do not dispatch or advance another role yourself.

## The Claim-to-Evidence Gate

Before a positive claim:

1. **Claim:** State exactly what is complete, fixed, passing, or ready, and identify the candidate being evaluated.
2. **Risks:** List every risk directly covered by that claim: changed behavior, direct consumers, state or persistence boundaries, artifact identity, scope, and any external, device, or human gate.
3. **Oracles:** Select a real oracle for each applicable risk.
4. **Fresh run:** Run the smallest complete set of selected commands and evidence steps against the current candidate.
5. **Full result:** Let each selected command finish; read its complete relevant output, exit code, failure and warning counts, and produced artifact identity.
6. **Honest state:** Make only the claim the evidence supports. Otherwise report the actual result, missing gate, and recovery condition.

Old output, another candidate's artifact, source inspection alone, or confidence is not fresh evidence.

## Complete Command vs. Complete Risk Set

A **complete selected command** is one chosen oracle run from start to terminal exit without truncating it, stopping after a favorable line, or extrapolating from a subset.

The **claim-bound minimum complete risk set** is the collection of commands and evidence steps needed to cover every applicable risk in the exact claim. It may contain a focused test plus directly affected regressions, a build plus an artifact identity check, or a device or human gate in addition to automation.

These concepts are complementary. Neither means “run the entire repository by default.” Run a repository-wide suite only when the governing task, an accepted project gate, or demonstrated risk propagation requires it. Never call a focused set “all tests.”

## Size Evidence by Demonstrated Risk Propagation

Choose the amount of testing and verification from the semantic risk propagation, not from character count, diff size, file count, or whether the edit looks simple. Before execution, identify how the changed behavior can propagate through accepted ownership, direct consumers, public contracts, state, persistence, concurrency, packaging, and real external boundaries. Support that propagation map with the accepted contract, dependency or call paths, persisted relationships, or an observed failure; do not expand validation merely because an effect is imaginable.

- For behavior whose propagation is bounded to a local owner and known consumers, run the decisive focused oracle plus the directly affected regressions, then stop.
- For shared core behavior, a public API, schema or migration, persistence, concurrency, cross-module state, or another wide boundary, extend evidence to every demonstrated affected consumer and boundary. Use a broader affected suite only to the extent that the propagation map reaches it.
- Run a repository-wide suite only when it is an explicit accepted gate, demonstrated propagation is repository-wide, or focused and directly affected evidence reveals that the claim cannot be covered by a narrower accepted suite. “Fresh,” “small edit,” uncertainty by itself, and desire for confidence are not reasons.
- Run device, performance, external-service, or human validation only when the claim or changed behavior reaches that real boundary or the accepted contract explicitly requires the gate.
- A non-executable change may need only its relevant parser, schema, format, diff, or identity oracle; a one-character executable change may require broad regression evidence. The semantic effect decides, not the form of the edit.

Record why the selected set is sufficient and what evidence would require expanding it. If a selected check exposes a wider causal effect, update the propagation map and add only the newly required evidence. Do not repeat an unchanged passing gate.

## Choose Oracles That Match the Risk

| Risk or claim | Direct evidence | Does not prove it |
|---|---|---|
| Consumer behavior | Focused RED/GREEN plus directly affected regression | Source text or compilation alone |
| Compilation/build | Fresh required build with exit 0 | Lint or unit tests alone |
| Artifact correctness | Fresh artifact plus identity and relevant inspection/run | An older artifact or source diff |
| Scope/protected state | Candidate diff, index, and protected-state comparison | Passing behavior tests |
| External integration | Real boundary response and original error handling | A permissive mock |
| Production wiring | Production-path integration evidence | An injected seam, fake, or no-op |
| Physical device | Identity-bound physical-device evidence | Unit test, source inspection, or emulator |
| Human experience | The specified human acceptance | Screenshot existence or automated assertion |
| Requirements | Acceptance-to-evidence walkthrough | A keyword, regex, or format validator |

Automated evidence proves only its layer. Preserve required identity-bound Reviewer, physical-device, and human gates; a Writer's verification does not complete them.

## Candidate and Baseline Discipline

Verify against the immutable candidate identity when the workflow provides one. Rebuild a corresponding artifact when the accepted claim includes that artifact, the contract requires the build gate, or demonstrated propagation reaches compilation, packaging, installation, or runtime construction. Do not rebuild every artifact merely because some executable source changed.

For any failure or warning, determine whether the candidate introduced it. A candidate regression within scope blocks the claim and must be fixed. A proven pre-existing or unrelated failure is preserved and disclosed; it does not authorize unrelated changes and prevents only claims that include the failing set.

A warning blocks completion only when the candidate introduced it, it makes a required command fail, or the accepted contract forbids it. Otherwise report it accurately without claiming pristine global output.

## Before Commit, Push, or Terminal Report

Verify every acceptance criterion with its actual oracle, not merely a passing test count. Check the exact candidate diff and allowed paths, format or artifact requirements, index state, protected state, and remote identity required by the role contract. Read the complete results before committing; after a commit or push, verify the new immutable identity and remote state where required.

Do not claim an unperformed Reviewer, merge, physical-device, human, Android, or external gate. Do not move to the next role yourself when the governing workflow assigns that responsibility elsewhere.

## Stop and Failure Signals

Stop and report the actual state when an oracle cannot run, its output is incomplete, the candidate identity is uncertain, a required evidence layer is unavailable, or verification would expand scope or authority.

Failure signals include: “should” or “probably” replacing a run, a partial command represented as complete, a large unrelated suite substituted for the direct oracle, a successful build represented as behavior proof, an emulator represented as a physical device, old evidence reused for a new candidate, or a Writer represented as an independent Reviewer.

Once every accepted claim has one fresh risk-matched proof and all required gates are satisfied, stop. Do not repeat a passing command when the candidate and relevant environment are unchanged, add a broader suite for appearance, hash unrelated files, or manufacture extra evidence. A new failure returns to the authorized implementation or diagnostic role; an unapproved write, evidence layer, or decision returns `SCOPE_EXPANSION_REQUIRED` or the role contract's blocked terminal.
