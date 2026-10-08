---
name: test-driven-development
description: Use for approved behavior changes and bug fixes that can be exercised before implementation; use the governing contract's real artifact or device oracle when a production unit test cannot prove the change.
---

# Test-Driven Development

## Story实施、审查与修复边界

1. **首次Writer完整实现批准的Story**，把范围内的行为和接线做完整。
2. **首次Reviewer独立完整审查；后续Reviewer只检查当前批准的修复及其明确影响。** 原来通过的审查结论和测试结果按原范围保留，不自动失效、不重复审查或重跑。
3. **Repair Writer严格按批准内容修改。** 指定的问题、路径和验证范围就是边界；需要改别处或增加验证，先说明并取得批准，不能借“完整原因链”自行越界。

首次完整检查应覆盖批准范围内的实际行为和必要直接接线；后续Review只完成当前批准修复及明确影响的审查，继承原范围内已通过的结论和测试。完整提示词、完整报告和fresh Reviewer均不表示重审整个Story或重跑旧测试。

## Purpose and Authority

Use strict RED → GREEN → REFACTOR to prove an approved behavior change. This skill supplies a method; it does not grant scope, permissions, architecture changes, or a new evidence standard.

Before changing a test or implementation, apply the governing authority in this order:

1. user, system, and developer instructions;
2. the repository instructions and complete role contract;
3. the immutable task, finding batch, and evidence contract;
4. accepted product, data, and code contracts;
5. this method.

Record the exact candidate and allowed paths, accepted behavior and non-goals, contract-excluded states, observable success and failure, pre-existing failures or warnings, required evidence layer, and protected or unrelated state. Stop if any of these cannot be determined without a new scope, ownership, architecture, or evidence decision.

## 用户流程与最小必要检查

以下规则约束本文件中的完整读取、身份核验、独立核对和交付检查，不新增审批层、报告文件、测试或检查轮次。
1. 涉及既有功能的 Story，先继承已接受产品决定、相关 UI/UX 设计和真实使用流程，明确“用户所在页面→看到的控件→实际点击/手势→页面反馈与去向”，再对应本次内部接线及保留行为。交接必须给出准确来源和必要章节；单条测试流程、源码调用链或接口状态不能代替整个 Story 的用户流程。只读相关片段，不为继承依据通读全部产品文档；已有决定直接沿用，真正冲突才讨论。
2. 疑问先说明具体用户操作链、当前影响及依据。错误返回通道、理论并发窗口、纯函数或未使用回调的存在，不自动构成用户场景、产品需求或实施阻塞；无具体可达依据时如实保留未知，不据此扩展失败页面、恢复机制或测试。实际正常操作出现接线缺陷应修正接线，不以失败提示替代修复；不吞错、不把未证实说成不可能。
3. 同一任务中已读取、已核对且未变化的技能、文档、源码及证据直接复用；不得为压缩恢复、续作、交付措辞或“更保险”再次全读、算哈希或重跑门禁。提示词模板适用下一条的每次必读例外。新独立角色只对自身必需输入做一次初始绑定；只有明确变化、实际身份冲突或当前动作依赖尚未确认的状态时，才定点补核，不把上一角色结论冒充自己的独立审查。
4. 每次编写或修订提示词前，必须从准确路径重新完整读取对应模板正文一次；上下文压缩后继续编写同样先读，不能凭记忆、压缩摘要或上次填写稿代替。此要求仅授权读取模板，不自动触发模板完整性审计、哈希核验、Git检查或其他来源重读。未修改原模板时，不重新审计其正文完整性。新生成提示词只对本次填写/修改内容及其必须保留的规则做一次必要检查；不能把原样保留模板变成全文反复比对任务。交接检查首先确认用户流程、已有决定、此次改动及直接消费者的对应关系；占位符清零、哈希一致和格式完整不能代替这项判断。
5. Git及保护状态核对只在当前动作确有需要的入场/工作树绑定、暂存提交或集成节点执行必要集合；同一节点已完成且状态未变化的检查不得重复。规划续作、普通答疑、文案整理不得自动触发整套Git、哈希或保护资产审计；不取消已批准且尚未完成的必要门禁。
6. 搜索先限定直接相关文件、章节和符号；长文档先定位再取片段，不用宽泛关键词跨大量历史全文输出。已有证据足够回答或完成当前修改立即停止；输出过宽时收窄，不追加更大调查。不得为证明自己检查过而创建额外清单、脚本、报告或测试。
7. 发生交接失误时，依据实际记录说明遗漏和影响；不能未经检查就宣称整段实现都在猜、全部无效或必须重开。保留已完成工作，只修正有依据的缺口。用户要求减少消耗时立即收窄或停止无必要操作，不能拿治理要求解释反复检查。

## 查证与复用边界

先查官方与现有能力，优先复用：
- 从需求澄清、方案设计和技术选型阶段就先查证，再确定设计与实现方案；实现、修复及缺陷判断同样遵循此规则，不以已经出现缺陷为查询前提。先定点查阅与实际版本有关的官方文档/源码、GitHub仓库及Issues、其他可靠网络资料和适用的成熟实现，不限于官方网站，并核对项目现有代码。优先原始来源和维护者资料，区分官方保证、维护者结论与社区经验，不把社区猜测当系统保证。明确系统默认行为、配置/API已经提供的能力，以及当前需求真正缺少的部分；不先假设需要自写逻辑。
- 优先复用系统能力、框架API和项目现有实现；确需引入成熟开源实现时核对适用版本与许可，不搬入整套无关架构。已有能力能满足需求时，不再自建等价owner、包装层、调度或恢复机制。
- 先确认真实用户入口和已接受需求。未使用回调、纯函数、框架API或潜在技术场景的存在，不证明有用户可触发的缺陷，也不授权新增入口、按钮或功能来制造迁移/测试的必要性。
- 简短交代来源链接/版本、复用能力及必须自写的部分和理由。同版本已核实资料直接复用；足够回答当前问题即停止搜索，不新增研究轮次、不重读全部历史。资料不足或冲突时明确UNKNOWN/CONFLICT，不猜成事实，不把默认行为说成所有版本/设备上的保证。
- 网上查到的任何可复用、可替代、可参考或可直接使用的方案，在纳入设计、技术选型或实施之前，都必须先与用户讨论：说明来源、适用条件、解决什么问题、复用/替代/参考/直接采用的具体方式、收益与代价，以及对当前范围和验证的影响；取得用户对准确方案的明确同意后才落实。即使属于原范围、只作参考、只是系统配置或看似等价替换，也不能自行决定采用。
- 查阅、核对和比较资料可以先进行，讨论前可形成可审阅的方案说明；不得先修改产品代码、接入依赖或替换已批准设计。已经讨论并明确批准的准确方案继续执行，不重复审批；来源发生变化但方案与批准边界未变时复用原批准，方案或边界改变则先讨论并获准。网上建议和示例不是用户需求或实施授权。
- 网上建议和示例不是需求或权限。新增/升级依赖、安装工具、产品/架构/生命周期改变、额外路径及验证增量，仍受下列越界门禁约束；源码/API/hash只能证明其对应层，不能冒充实际运行。

执行RED或新增测试前仍须遵守用户已批准的验证集合；本技能的方法不授权为已由系统满足的行为制造测试或重复实现。

越界立即停止与完整报告：
- 一旦判断下一步超出已获准确授权的需求、范围、包数、写路径、owner、生命周期、接口、数据责任、依赖或环境，或需要新增/改变测试方法、同方法内的场景/输入/步骤/断言、fixture、调度、callback、等待、超时、命令或回归，必须在相关新增工作、修改或运行前停止，保留现场与有效证据。
- 技能、模板、Review、因果必要性、风险传播、“完整性”“更保险”“最佳实践”均不能代替用户批准。本门禁同样约束后文关于扩大诊断/验证或重新运行的表述；已获准确批准的范围无需重复审批。
- 交回主管理的报告一次写清六点：
  1. 具体问题、文件/方法和实际行为，区分PROVEN、INFERENCE、UNKNOWN。
  2. 原定工作已完成和已证明的内容。
  3. 具体缺少哪项行为证明或合同依据。
  4. 拟增加的准确路径、输入、步骤、断言、设施或命令及各自用途。
  5. 原范围为什么不能解决，不增加会留下什么实际缺口。
  6. 当前改动、产物、证据、未完成事项及获批后的唯一下一动作。
- 标记角色对应的BLOCKED/REVIEW_BLOCKED，不声称完成或全部通过；未获用户明确批准不得执行增量，不能通过其他角色绕过。获批后只执行准确批准范围。Reviewer可完成其余已授权审查，但不得把待批准增量写成Repair必须执行的要求。
- 不循环调整fixture/调度/等待/超时，不重复命令碰运气，不新增生产test seam，不削弱断言、改变输入或事务边界绕过失败。产品、设施和环境失败必须分清。
- 已通过且未受影响的结果继续有效；只复验准确修复对应的已批准集合，不因局部修改重跑整批，不在交付前追加测试、build、设备、性能或人工门禁。

## Lifecycle and transitions

Use this state sequence and do not skip a transition:

```text
BOUND -> RED_PROVEN -> GREEN -> REFACTORED -> VERIFIED -> RETURN
```

- `BOUND`: the approved behavior, current candidate, scope, non-goals, oracle, evidence budget, and protected state are fixed.
- `RED_PROVEN`: the chosen oracle fails for the intended missing behavior. A broken fixture, environment failure, or unrelated baseline is not this state.
- `GREEN`: the minimum causal implementation passes the same oracle without weakening it.
- `REFACTORED`: only affected structure was improved and the oracle stayed green. This state may be skipped when no cleanup is needed.
- `VERIFIED`: the directly affected regression set and every contract-required real-boundary gate have fresh evidence. Use `../verification-before-completion/SKILL.md` for this transition.
- `RETURN`: report the actual terminal to the governing role; do not dispatch a Reviewer, merge, or start another Story.

An unexpected or unexplained failure transitions to `../systematic-debugging/SKILL.md`; an expected meaningful RED does not. A structure-only or external-boundary change uses the accepted real oracle and records why an automated RED is inapplicable.

Read-only investigation may inspect adjacent code, but necessity is not write authority. An additional write path is allowed only when the filled role contract already authorizes causal expansion or an exact amendment is accepted before editing. If the change introduces a new product, architecture, ownership, schema, migration, dependency, public-interface, security, or evidence decision, return `SCOPE_EXPANSION_REQUIRED` without a partial workaround.

## When the Cycle Applies

Use strict TDD by default for behavior changes and bug fixes whose result can be exercised by an automated oracle. Refactoring belongs in the REFACTOR phase after behavior is protected; do not fabricate a new failing behavior for a structure-only change.

Pure documentation, metadata, non-executable artifacts, and behavior provable only at an external or physical boundary do not earn a fabricated production unit test. Use the real oracle required by the governing contract—such as schema validation, compilation, rendering, artifact comparison, an integration run, a physical-device step, or a human gate—and disclose the TDD exception.

When accepted implementation already exists, preserve it. First establish a regression or characterization oracle for the approved new behavior, then make the smallest causal change. Do not delete accepted, user-authored, protected, or pre-existing code to recreate a clean-slate TDD sequence.

## The Strict Cycle

### RED — Prove the Missing Behavior

Write one focused test for one consumer-observable behavior or real invariant. Before implementation:

1. state the production mutation or missing behavior the test should detect;
2. use an expectation derived independently from the code under test;
3. run the focused test and read its relevant output and exit status;
4. confirm it fails because the approved behavior is missing.

A syntax error, broken fixture, unavailable environment, or unrelated baseline failure is not RED. If the test passes unexpectedly, investigate existing behavior or the oracle; do not proceed to GREEN until the failure is meaningful.

### GREEN — Implement the Minimum Causal Behavior

Implement the smallest complete change for the approved behavior, including necessary direct callers, data handling, and UI wiring. Do not leave half a feature to reduce file count. Do not add future options, unrelated cleanup, or speculative abstractions. Validation stays within the approved set; explain an actual failure before proceeding, and do not obtain GREEN through repeated unchanged runs, changed inputs, weaker assertions, or longer waits.

Rely on explicit user decisions, types, database constraints, and current framework guarantees; do not present guesses as facts or invent blockers from unknowns. Validate at the place responsible for accepting data or enforcing a rule, including required business-state checks. Do not repeat a check downstream while its guarantee remains valid. Reuse accepted error handling, preserve the original cause, and perform required cleanup; catching an error is not itself swallowing it. Never turn failure into success, an empty result, or a default, and do not invent failure screens from an error channel.

Run the focused test again. If it still fails, change the implementation or correct a proven oracle defect—never weaken the accepted assertion merely to obtain GREEN.

### REFACTOR — Improve Only the Affected Structure

After GREEN, improve names or remove duplication only within the affected structure. Do not add behavior. Re-run the focused test after each meaningful refactor.

Then run the directly affected regression set: consumers, state transitions, persistence or boundary contracts that the change can actually influence. Establish that influence from the accepted contract, owner/consumer paths, state or persisted relationships, public boundaries, or an observed failure—not from diff size or imagined possibility. A repository-wide suite is required only when it is an accepted gate, propagation is demonstrated as repository-wide, or narrower affected evidence proves unable to cover the claim.

## Existing Work and Code-First Recovery

Code that existed before the current attempt—accepted base content, user dirty work, another candidate, or protected state—must remain intact. Process only the approved behavior or complete finding batch. A function or module may express a current responsibility even with one caller. Prefer existing capabilities; add structure only for a concrete present need, not hypothetical reuse. This applies to both existing-code changes and new projects and does not expand approved paths or test facilities.

If the current agent wrote implementation before RED, removal is allowed only when every removed line is precisely attributable to the current agent's current undelivered attempt, has not been delivered or adopted by accepted work, is not protected, and has no accepted consumer or dependency. Preserve all other content and remove the attributable change with a scoped edit, never a destructive Git reset or checkout. Then establish RED. Local commit or push status alone does not define delivery or adoption.

Exploration may be discarded only when it was identified in advance as temporary, was created by the current task, has not been delivered or adopted by accepted work, and has no accepted consumer or dependency. Its removal remains subject to the scoped-edit and protected-state limits above regardless of local commit status.

## Test Selection and Evidence Layers

Test observable contracts rather than private calls, mock existence, framework guarantees, or method presence. Trivial forwarding, data holders, and generated code need no test of their own; cover the first consumer-visible outcome. A new function does require coverage when it owns an observable branch, state transition, side effect, or error contract.

Derive edge and error cases only from the accepted contract, a real boundary, or a demonstrated failure. If the contract excludes null, default, malformed, or other states, do not add tests, guards, or fallback behavior for them.

Mocks and fakes may isolate an uncontrollable external boundary, but prove only the injected layer. Unit tests, source inspection, fakes, and emulators do not prove production wiring, a physical device, or human experience. Preserve every identity-bound external or human gate.

For detailed test construction, read [writing-good-tests.md](writing-good-tests.md) when writing or changing tests, mocks, fixtures, or test helpers.

## Baseline and Completion

Candidate-introduced regressions must be fixed inside the approved scope. For a pre-existing or unrelated failure or warning:

1. reproduce or otherwise identify the baseline;
2. compare it with the candidate result;
3. preserve evidence and report it without changing unrelated code;
4. avoid any claim that the unrun or failing larger set passed.

Before claiming the TDD cycle complete, the meaningful RED must have been observed, the same oracle must be GREEN on the current candidate, the directly affected regression set must be fresh, and every required real-boundary gate must be accurately reported. Stop rather than expanding scope when the complete fix would require a new owner, schema, core interface, cross-module responsibility, or architecture decision.

Define the claim-to-evidence set before running validation. Focused and directly affected checks are the default. Size the set by demonstrated semantic risk propagation, never by character count, file count, or apparent simplicity. Do not add a repository-wide suite, device run, performance series, artifact rebuild, or repeated passing gate merely for confidence or appearance; run it only when the accepted contract or demonstrated propagation reaches that boundary. Stop the cycle when every accepted claim has one fresh risk-matched proof and all required gates are satisfied.
