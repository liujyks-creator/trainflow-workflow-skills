---
name: systematic-debugging
description: Use after a bug, test failure, build failure, or unexpected behavior is observed, before proposing a fix; traces evidence to a falsifiable root cause without expanding task scope.
---

# Systematic Debugging

## Purpose and Authority

Debug by moving from evidence to pattern to one falsifiable hypothesis to one causal fix. Do not propose or implement a fix before locating the earliest supported cause.

This skill is a diagnostic method, not scope, permission, architecture, or evidence authority. First apply user and system instructions, repository and role contracts, the immutable task or complete finding batch, and accepted code or product contracts. Then record:

- the exact candidate, allowed paths, protected state, and current failure;
- accepted behavior, non-goals, and contract-excluded states;
- stable reproduction or the specific unknown preventing it;
- pre-existing failures and warnings;
- the evidence layer and observable success signal.

If the complete fix needs a new owner, schema, core interface, cross-module responsibility, architecture decision, or unapproved path, stop and return the evidence to the governing workflow.

## 查证与复用边界

先查官方与现有能力，优先复用：
- 从需求澄清、方案设计和技术选型阶段就先查证，再确定设计与实现方案；实现、修复及缺陷判断同样遵循此规则，不以已经出现缺陷为查询前提。先定点查阅与实际版本有关的官方文档/源码、GitHub仓库及Issues、其他可靠网络资料和适用的成熟实现，不限于官方网站，并核对项目现有代码。优先原始来源和维护者资料，区分官方保证、维护者结论与社区经验，不把社区猜测当系统保证。明确系统默认行为、配置/API已经提供的能力，以及当前需求真正缺少的部分；不先假设需要自写逻辑。
- 优先复用系统能力、框架API和项目现有实现；确需引入成熟开源实现时核对适用版本与许可，不搬入整套无关架构。已有能力能满足需求时，不再自建等价owner、包装层、调度或恢复机制。
- 先确认真实用户入口和已接受需求。未使用回调、纯函数、框架API或潜在技术场景的存在，不证明有用户可触发的缺陷，也不授权新增入口、按钮或功能来制造迁移/测试的必要性。
- 简短交代来源链接/版本、复用能力及必须自写的部分和理由。同版本已核实资料直接复用；足够回答当前问题即停止搜索，不新增研究轮次、不重读全部历史。资料不足或冲突时明确UNKNOWN/CONFLICT，不猜成事实，不把默认行为说成所有版本/设备上的保证。
- 网上查到的任何可复用、可替代、可参考或可直接使用的方案，在纳入设计、技术选型或实施之前，都必须先与用户讨论：说明来源、适用条件、解决什么问题、复用/替代/参考/直接采用的具体方式、收益与代价，以及对当前范围和验证的影响；取得用户对准确方案的明确同意后才落实。即使属于原范围、只作参考、只是系统配置或看似等价替换，也不能自行决定采用。
- 查阅、核对和比较资料可以先进行，讨论前可形成可审阅的方案说明；不得先修改产品代码、接入依赖或替换已批准设计。已经讨论并明确批准的准确方案继续执行，不重复审批；来源发生变化但方案与批准边界未变时复用原批准，方案或边界改变则先讨论并获准。网上建议和示例不是用户需求或实施授权。
- 网上建议和示例不是需求或权限。新增/升级依赖、安装工具、产品/架构/生命周期改变、额外路径及验证增量，仍受下列越界门禁约束；源码/API/hash只能证明其对应层，不能冒充实际运行。

先用版本对应的官方保证与真实调用链区分产品缺陷、正常系统行为、设施和环境问题。诊断所需的新probe、日志、等待或命令同样需要准确授权，不因Phase 1–4或尝试次数上限获得试错许可。

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

```text
OBSERVED -> REPRODUCED -> ROOT_CAUSE_SUPPORTED -> ORACLE_ESTABLISHED
-> FIX_GREEN -> VERIFIED -> RETURN
```

- Remain in `OBSERVED` while reproduction is unstable; report the exact unknown instead of guessing.
- Enter `ROOT_CAUSE_SUPPORTED` only when evidence locates the earliest controllable wrong state and distinguishes it from competing explanations.
- `ORACLE_ESTABLISHED` is a meaningful failing regression or the accepted real-boundary oracle.
- `FIX_GREEN` contains one minimum causally complete change at the supported source.
- `VERIFIED` uses `../verification-before-completion/SKILL.md` with the directly affected risk set.
- `RETURN` reports evidence and the actual state to the governing role; it does not dispatch, merge, or widen the assignment.

Read-only tracing may cross the expected modification set. A write outside the authorized set requires an explicit causal-expansion permission or exact accepted amendment before editing. A new product, architecture, ownership, schema, migration, dependency, public-interface, security, or evidence decision transitions to `SCOPE_EXPANSION_REQUIRED`; do not route around it with a wrapper, adapter, fallback, duplicate authority, or partial symptom fix.

## Phase 1 — Evidence and Root Cause

Read the complete relevant error, stack, exit code, warning, and artifact identity. Reproduce the symptom with exact inputs and environment when possible. Check the candidate delta and relevant recent change rather than assuming temporal correlation is causation.

Choose the smallest oracle that reproduces the real failure:

- an existing test and runner filter;
- a repeatable command and its exit or output;
- an artifact diff or schema/render/build check;
- a boundary trace of input, output, and state;
- an integration, emulator, physical-device, or human step when that is the actual boundary.

The absence of a test framework does not require a one-off script. If reproduction is unstable, state the unknown and gather evidence that distinguishes hypotheses; do not guess-fix.

For a deep symptom or suspected test pollution, read [root-cause-tracing.md](root-cause-tracing.md).

### Boundary Instrumentation

Instrument only boundaries relevant to competing explanations. Capture the minimum safe values needed to show where correct state becomes incorrect. Never log secrets, credentials, personal data, or sensitive health data. Prefer existing logging and runner facilities; do not create a one-use helper, wrapper, script, manager, or monitoring owner for a single investigation.

Mark temporary probes as task-owned and remove them after the hypothesis is resolved unless the governing task explicitly adopts them as durable telemetry. The probe's output is evidence, not a production fix.

## Phase 2 — Pattern

Find a working comparator governed by the same contract. Read the relevant implementation and configuration completely enough to understand its lifecycle. List every observed difference between working and failing cases, including inputs, owner, timing, state, environment, and evidence layer. Do not dismiss a difference until evidence makes it irrelevant.

The output of this phase is a ranked set of factual differences, not a list of proposed fixes.

## Phase 3 — One Hypothesis

State one hypothesis in falsifiable form:

```text
Cause: X is the earliest wrong state.
Because: evidence Y shows the preceding boundary is correct and this boundary is not.
Probe: change or observe one variable Z.
Expected result: observation Q confirms it; observation R rejects it.
```

Run the smallest safe probe and read the result. If rejected, remove or revert only the task-owned probe, update the evidence ledger, and form a new hypothesis. Do not stack multiple speculative changes.

## Phase 4 — Causal Fix and Regression

After a root cause is supported, establish the correct failing regression or other real oracle. For an automated behavior, use strict RED → GREEN → REFACTOR. For a document, artifact, external service, or physical behavior, use the contract's actual oracle and disclose the evidence layer.

Implement one minimum causally complete fix at the earliest controllable source. Do not add unrelated refactors, blanket validation, or any retry, fallback, silent default, broad catch, or future monitoring that the accepted contract does not require. Run the focused oracle and the directly affected regression set.

Candidate-introduced regressions must be repaired within scope. Prove, preserve, and report pre-existing or unrelated failures; do not fix them or claim the unrun larger suite passed.

## External and Environment Failures

For a network, SDK, environment, or device failure, preserve the original signal and identify the failing real boundary. Add error mapping, retry, timeout, fallback, or monitoring only when the accepted contract explicitly requires that behavior at that boundary. Otherwise report the external blocker and recovery condition. An injected fake, source inspection, or emulator result cannot replace required production, physical-device, or human evidence.

## Repair Findings

When debugging an approved repair batch:

1. read the complete batch and restate each technical claim;
2. reproduce or inspect the exact candidate evidence for every claim;
3. identify shared causes before editing;
4. if valid, address the complete atomic batch within its authority;
5. if invalid or unprovable, report the contrary or missing evidence without changing correct code.

Do not blindly implement reviewer wording, fix only the first item, or treat a finding as permission to widen scope.

## Stop Rules and Failure Signals

After each failed local fix attempt, return to Phase 1 with the new evidence. After three evidence-backed local fixes fail, do not attempt a fourth patch. Stop, summarize the attempts and observations, and escalate the architecture, owner, test seam, or problem definition to the governing workflow or Correct Course.

Immediate failure signals are: a proposed fix without root-cause evidence, multiple variables changed in one probe, an unstable oracle represented as fact, temporary instrumentation left behind, a swallowed external error, evidence-layer substitution, or scope expansion.

For timing and flakiness, read [condition-based-waiting.md](condition-based-waiting.md).

Define the minimum diagnostic and verification evidence before running it. One stable reproduction and one discriminating probe are enough when they support the cause. Expand diagnostics or regression coverage only when accepted dependency, ownership, state, persistence, boundary, or observed-failure evidence demonstrates wider propagation; change size and uncertainty alone do not. Do not repeat passing gates, collect unrelated logs, scan the repository for similar issues, or run broad suites merely for confidence. Stop when the root cause is supported, the causal fix is verified by the accepted oracle, and every required gate is satisfied.
