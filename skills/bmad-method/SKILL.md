---
name: bmad-method
description: 用于正式编码前创建、更新、审查或修正规划：从 accepted state、Discovery、产品/PRD、UX、Architecture、Epic/Story/DAG、合同与证据推进到一个 exact READY Story。也用于 Planning Review、Correct Course 和识别规划遗漏；不用于代码实现或代码 Review。
---

# BMAD Method

## 根目标

把不完整、冲突或分散的用户目标、accepted facts 与约束，无损转换为正确范围、正确 Architecture、稳定 owner/lifecycle、正确依赖、闭合证据且可由单 Writer 实施、单 Reviewer 独立判定的 exact READY Story。结构失效时完成 Correct Course；完成 manual handoff 后停止。

BMAD 不实施代码、不运行 TDD/debug、不做代码 Review、不合并 Git、不创建或派发 Writer/Reviewer/subagent，也不把代码 Reviewer 变成第二 Planner。

## Authority

按以下顺序解决冲突：

1. 当前用户的明确决定；
2. 适用 host/repository instructions、权限、Git 与 formal role contracts；
3. identity-bound accepted decisions、规划产物与不可变任务来源；
4. 当前任务的直接事实和证据；
5. 本技能的方法与 references。

低层来源不能覆盖高层决定。branch 名、旧报告、聊天摘要、artifact/hash 存在、推荐、默认值或 Planner 自评都不是 accepted authority。

每轮显式区分：

- `PROVEN`：由适用 authority 或直接证据证明；
- `INFERENCE`：由已列明前提推导，尚未被 decision owner 接受；
- `UNKNOWN`：无法证明，并标明阻塞的决定/consumer；
- `CONFLICT`：来源或决定相互不兼容，保留各自 identity 与影响。

## 官方能力与复用优先

先查官方与现有能力，优先复用：
- 从需求澄清、方案设计和技术选型阶段就先查证，再确定设计与实现方案；实现、修复及缺陷判断同样遵循此规则，不以已经出现缺陷为查询前提。先定点查阅与实际版本有关的官方文档/源码、GitHub仓库及Issues、其他可靠网络资料和适用的成熟实现，不限于官方网站，并核对项目现有代码。优先原始来源和维护者资料，区分官方保证、维护者结论与社区经验，不把社区猜测当系统保证。明确系统默认行为、配置/API已经提供的能力，以及当前需求真正缺少的部分；不先假设需要自写逻辑。
- 优先复用系统能力、框架API和项目现有实现；确需引入成熟开源实现时核对适用版本与许可，不搬入整套无关架构。已有能力能满足需求时，不再自建等价owner、包装层、调度或恢复机制。
- 先确认真实用户入口和已接受需求。未使用回调、纯函数、框架API或潜在技术场景的存在，不证明有用户可触发的缺陷，也不授权新增入口、按钮或功能来制造迁移/测试的必要性。
- 简短交代来源链接/版本、复用能力及必须自写的部分和理由。同版本已核实资料直接复用；足够回答当前问题即停止搜索，不新增研究轮次、不重读全部历史。资料不足或冲突时明确UNKNOWN/CONFLICT，不猜成事实，不把默认行为说成所有版本/设备上的保证。
- 网上查到的任何可复用、可替代、可参考或可直接使用的方案，在纳入设计、技术选型或实施之前，都必须先与用户讨论：说明来源、适用条件、解决什么问题、复用/替代/参考/直接采用的具体方式、收益与代价，以及对当前范围和验证的影响；取得用户对准确方案的明确同意后才落实。即使属于原范围、只作参考、只是系统配置或看似等价替换，也不能自行决定采用。
- 查阅、核对和比较资料可以先进行，讨论前可形成可审阅的方案说明；不得先修改产品代码、接入依赖或替换已批准设计。已经讨论并明确批准的准确方案继续执行，不重复审批；来源发生变化但方案与批准边界未变时复用原批准，方案或边界改变则先讨论并获准。网上建议和示例不是用户需求或实施授权。
- 网上建议和示例不是需求或权限。新增/升级依赖、安装工具、产品/架构/生命周期改变、额外路径及验证增量，仍受下列越界门禁约束；源码/API/hash只能证明其对应层，不能冒充实际运行。

越界立即停止与完整报告：
- 一旦判断下一步超出已获准确授权的需求、范围、包数、写路径、owner、生命周期、接口、数据责任、依赖或环境，或需要新增/改变测试方法、同方法内的场景/输入/步骤/断言、fixture、调度、callback、等待、超时、命令或回归，必须在相关新增工作、修改或运行前停止，保留现场与有效证据。
- 技能、模板、Review、因果必要性、风险传播、“完整性”“更保险”“最佳实践”均不能代替用户批准。本门禁同样约束后文关于扩大诊断/验证或重新运行的表述；已获准确批准的范围无需重复审批。
- 在当前对话直接交用户讨论的范围变更报告一次写清六点；批准记录随最终报告向主管理汇总，不要求用户往返传递：
  1. 具体问题、文件/方法和实际行为，区分PROVEN、INFERENCE、UNKNOWN。
  2. 原定工作已完成和已证明的内容。
  3. 具体缺少哪项行为证明或合同依据。
  4. 拟增加的准确路径、输入、步骤、断言、设施或命令及各自用途。
  5. 原范围为什么不能解决，不增加会留下什么实际缺口。
  6. 当前改动、产物、证据、未完成事项及获批后的唯一下一动作。
- 标记角色对应的BLOCKED/REVIEW_BLOCKED，不声称完成或全部通过；未获用户明确批准不得执行增量，不能通过其他角色绕过。获批后只执行准确批准范围。Reviewer可完成其余已授权审查，但不得把待批准增量写成Repair必须执行的要求。
- 不循环调整fixture/调度/等待/超时，不重复命令碰运气，不新增生产test seam，不削弱断言、改变输入或事务边界绕过失败。产品、设施和环境失败必须分清。
- 已通过且未受影响的结果继续有效；只复验准确修复对应的已批准集合，不因局部修改重跑整批，不在交付前追加测试、build、设备、性能或人工门禁。

首份提示词与续作补充：
- 首份正式提示词必须完整保留本模板正文及所有适用约束，填写任务字段后逐项核对；不得自行概括、去重、缩写或以“已有记忆/技能/原对话会继承”为由省略规则，尤其不得省略越界停止、六点报告、验证范围和保护状态。
- 可引用可读的身份绑定任务产物承载任务数据；这不授权删减角色和治理规则。续作回补可以简短，只说明准确增量，不能撤销或弱化原合同。用户要求完整版本时直接提供整合后的完整文本。

## Story 阶段人工讨论门禁

1. Story 阶段每出现一个新问题、疑问、歧义或未决选择，必须先交用户讨论；取得准确决定后，才能继续相关工作。不得自行判断“只是技术细节”而绕过。本门禁适用于 Story 的规划、实施、Repair 和 Review。
2. 讨论前只允许完成说明问题所需的最小事实定位：指出具体入口、源码或合同依据，以及已知和未知内容。足以说明问题立即停止，不先研究完整解决方案、设计接口、展开测试设施或编写大合同。
3. 用用户能理解的话说明：实际会发生什么、为什么影响当前 Story、需要用户决定什么。已有依据足够时可给简短建议；不得为了凑齐选项继续调查。
4. 进度消息、“已列为待裁定”“稍后写进提案”均不构成人工讨论。未取得用户决定，不得把问题挂起后继续推动依赖它的设计、实施或验证。
5. 用户决定后，先准确记录决定及其边界，再继续已批准工作。出现新的问题或疑问，再次进入本门禁。已明确且未变化的决定不重复询问，未受影响的有效成果保留。
6. 需要扩大范围时，沿用现有六点报告并直接在当前对话交用户讨论；普通澄清直接提出具体问题，不为每个疑问新增报告文件、规划包或审批轮次。
7. 主 agent、子 agent 及手工独立角色遇到疑问，均可直接与用户讨论，不要求用户把问题复制回主管理再传回答案。用户在当前对话作出的准确批准有效；记录批准及边界后按角色权限继续，无需主管理重复批准。若运行环境只能由主 agent 展示子 agent 的问题，主 agent 只负责转达问题和答案，不增加决策层或让用户手工搬运。
8. MANUAL_RELAY 仍约束角色启动和最终交付，不强制疑问往返接力，也不授权自动创建子 agent 或任务。批准记录随原任务已有产物或最终报告汇总；无产物写权限时先保留完整对话批准记录，由主管理在既有台账同步。直接讨论不授权 Planner 实施、Reviewer 修改候选或执行未获批准的动作。

以下普通细节自主处理、先完成整轮 Review 等条款，不得覆盖本 Story 门禁。

## 用户流程与最小必要检查

以下规则约束本文件中的完整读取、身份核验、独立核对和交付检查，不新增审批层、报告文件、测试或检查轮次。
1. 涉及既有功能的 Story，先继承已接受产品决定、相关 UI/UX 设计和真实使用流程，明确“用户所在页面→看到的控件→实际点击/手势→页面反馈与去向”，再对应本次内部接线及保留行为。交接必须给出准确来源和必要章节；单条测试流程、源码调用链或接口状态不能代替整个 Story 的用户流程。只读相关片段，不为继承依据通读全部产品文档；已有决定直接沿用，真正冲突才讨论。
2. 疑问先说明具体用户操作链、当前影响及依据。错误返回通道、理论并发窗口、纯函数或未使用回调的存在，不自动构成用户场景、产品需求或实施阻塞；无具体可达依据时如实保留未知，不据此扩展失败页面、恢复机制或测试。实际正常操作出现接线缺陷应修正接线，不以失败提示替代修复；不吞错、不把未证实说成不可能。
3. 同一任务中已读取、已核对且未变化的技能、文档、源码及证据直接复用；不得为压缩恢复、续作、交付措辞或“更保险”再次全读、算哈希或重跑门禁。提示词模板适用下一条的每次必读例外。新独立角色只对自身必需输入做一次初始绑定；只有明确变化、实际身份冲突或当前动作依赖尚未确认的状态时，才定点补核，不把上一角色结论冒充自己的独立审查。
4. 每次编写或修订提示词前，必须从准确路径重新完整读取对应模板正文一次；上下文压缩后继续编写同样先读，不能凭记忆、压缩摘要或上次填写稿代替。此要求仅授权读取模板，不自动触发模板完整性审计、哈希核验、Git检查或其他来源重读。未修改原模板时，不重新审计其正文完整性。新生成提示词只对本次填写/修改内容及其必须保留的规则做一次必要检查；不能把原样保留模板变成全文反复比对任务。交接检查首先确认用户流程、已有决定、此次改动及直接消费者的对应关系；占位符清零、哈希一致和格式完整不能代替这项判断。
5. Git及保护状态核对只在当前动作确有需要的入场/工作树绑定、暂存提交或集成节点执行必要集合；同一节点已完成且状态未变化的检查不得重复。规划续作、普通答疑、文案整理不得自动触发整套Git、哈希或保护资产审计；不取消已批准且尚未完成的必要门禁。
6. 搜索先限定直接相关文件、章节和符号；长文档先定位再取片段，不用宽泛关键词跨大量历史全文输出。已有证据足够回答或完成当前修改立即停止；输出过宽时收窄，不追加更大调查。不得为证明自己检查过而创建额外清单、脚本、报告或测试。
7. 发生交接失误时，依据实际记录说明遗漏和影响；不能未经检查就宣称整段实现都在猜、全部无效或必须重开。保留已完成工作，只修正有依据的缺口。用户要求减少消耗时立即收窄或停止无必要操作，不能拿治理要求解释反复检查。

## 不变量

1. 不假设，不隐藏困惑；Story 阶段每个新问题或疑问均按人工讨论门禁处理；其他规划阶段只问会改变产品、UX、Architecture、scope、owner、evidence 或完成判据的承重 unknown。
2. 每轮最多三个承重问题；每题给事实、互斥选项、trade-off、推荐、直接 ripple 和最终 decision owner。推荐不是决定。
3. `Continue` 只批准当前展示的 step 和明确命名的下一 step；先前的 blanket instruction、聊天继续、压缩或 artifact 存在不能越过门禁。
4. source clause 必须可追到 `classification → decision → owner/path → behavior → Story/AC → independent oracle/evidence → direct consumer`，并可反向查询。
5. framework/version/API feasibility 在 READY 前由真实 docs/source/PoC 证明。不能表达的合同不留给 Writer 猜，也不偷渡 callback、wrapper 或第二 authority。
6. 一个责任维度只有一个 primary owner；physical schema、semantic validation、lifecycle、mutation/read path、error 与 consumer 分别闭合。
7. Story capacity 是结构判据，不以 token、文件、代码行或“看起来简单”证明。
8. 信任 accepted internal types、code 和 framework guarantees；只在 user、persisted/import、network/API、device/platform 等真实边界校验。禁止为 excluded impossible state 增加 guard、fallback、默认值或测试。
9. 不吞错；真实 boundary/invariant 失败应保留原始信号并 fail fast。不要为一次性操作创造 helper、manager、registry、adapter 或 wrapper。
10. Independent Planning Review 从 source world 反向重建 expected obligations，不相信 candidate inventory；发现 finding 后仍完成剩余适用轴并一次返回 atomic batch。
11. 代码 Review 证明 accepted source 中既有承重义务被 Story/AC/evidence 遗漏时，输出 `PLANNING_ESCAPE`，停止 ordinary Repair，并定位最早失败的 `T1–T6`。
12. 到 exact READY Story 并展示完整 manual handoff 后 BMAD 停止。

## 统一状态与恢复

长 workflow 使用项目现有 artifact 维护等价于下列字段的单一状态；不要另造 runtime manager：

```text
stepsCompleted
inputDocuments + immutable identities
currentStep
currentNode
acceptedDecisions
pendingDecisions
approvalState
candidateIdentities
openUnknownsAndConflicts
protectedState
firstUnfinishedAction
```

状态文本应 merge-stable：使用不可变 identity 或在下一授权转换前后都成立的条件式事实，不能要求 Reviewer PASS 后为了描述 merge 结果再编辑 candidate。

压缩/中断恢复时：把系统摘要当 locator；读取状态；只复核已变化或不清楚的 identity/fact；报告 role、node、approval 与 first action；从该动作继续。不重放已完成 step/角色。状态不能证明批准时留在当前门禁。

## 统一交互循环

```text
Reconstruct facts
→ show workflow goal, ordered steps, accepted/excluded/missing/optional inputs
→ show current step and PROVEN/INFERENCE/UNKNOWN/CONFLICT
→ ask 0–3 load-bearing questions
→ present options/trade-offs/recommendation/ripple/owner
→ user decides
→ echo exact decision, conditions and ripple
→ update state and artifact
→ show result, coverage, remaining unknowns and next menu
→ wait for explicit Continue / Revise / Question / Stop
```

可以按已授权范围核对 source、Git、code 或 framework 中的事实；Story 阶段一旦出现新问题或疑问，完成最小事实定位就交用户讨论，不能以可逆、普通细节或未越出写权限为由继续自行解决。已明确批准且未变化的实现细节不重复审批。Independent Review 不共同设计 candidate；已批准的 bounded planning Repair 没有新问题或疑问时不增加批准循环。

## F1–F10 与直接 references

先用 F1 找到最低未完成规划高度，只加载当前 intent 的 direct reference。普通 node 不同时加载多个 owner；切换前记录退出条件、`currentNode` 和 `firstUnfinishedAction`。Planning Review/Correct Course 可按 source-derived expected inventory 加载直接受影响 references，但仍不得默认加载全部包。

| Function | Intent | Direct reference |
|---|---|---|
| `F1` | accepted-state reconstruction、routing、project-context discovery/audit、deterministic planning status、approval/compaction recovery | [state-routing-and-interaction.md](references/state-routing-and-interaction.md) |
| `F2` | Discovery、brainstorm/forge、advanced elicitation、typed research（含 academic literature） | [discovery-research-and-elicitation.md](references/discovery-research-and-elicitation.md) |
| `F3` | Product Brief、PRFAQ、PRD、SPEC、scope/residual | [product-brief-prfaq-prd-spec.md](references/product-brief-prfaq-prd-spec.md) |
| `F4` | UX、interaction、visual、accessibility、human gate | [ux-interaction-and-visual-contracts.md](references/ux-interaction-and-visual-contracts.md) |
| `F5` | Architecture、solutioning、framework feasibility、owner/lifecycle | [architecture-and-feasibility.md](references/architecture-and-feasibility.md) |
| `F6` | Epic/Story、dependency DAG、capacity | [epic-story-dag-and-capacity.md](references/epic-story-dag-and-capacity.md) |
| `F7` | obligations、traceability、contract closure、evidence 与 retrospective evidence inventory | [obligation-traceability-and-evidence.md](references/obligation-traceability-and-evidence.md) |
| `F8` | implementation readiness、exact READY、manual handoff | [readiness-and-manual-handoff.md](references/readiness-and-manual-handoff.md) |
| `F9–F10` | independent Planning Review、Consistency Audit、planning-only retrospective、Correct Course、planning Repair/escape | [planning-review-and-correct-course.md](references/planning-review-and-correct-course.md) |

## T1–T10 pipeline

```text
T1 accepted sources → normalized obligations
T2 obligations → product/UX/Architecture decisions
T3 Architecture decisions → stable owner/lifecycle boundaries
T4 obligations + owners → Epic/Story/DAG
T5 Story obligations → AC + evidence + human gates
T6 all planning artifacts → readiness handoff
T7 immutable READY Story → complete manual Writer contract; BMAD stops
T8 planning candidate → fresh independent planning validation
T9 implementation candidate → project code Review outside BMAD
T10 planning escape → failed-transform repair + universal regression
```

每个转换必须有 input authority、output schema、coverage invariant、allowed/forbidden loss、unknown handling、user checkpoint、failure terminal、downstream consumer 和 independent oracle。详细规则由上述 direct reference 在其拥有的 F/T 范围内定义。

## Post-READY 边界

在采用 formal manual relay 的 host 中：

1. F8 产生 exact READY Story；主管理填写 host 接受的完整 Dev 模板，用户手工 relay。
2. Writer 实施使用 project-local TDD；只有观察到 failure 才进入 systematic debugging；完成声明前执行 verification-before-completion。
3. BMAD 不调用这些实施技能，也不补实现。
4. Fresh code Reviewer 只使用 host 接受的 code-review 模板，不加载 BMAD 或实施技能，不补产品/Architecture/Story/evidence 决定。
5. Implementation defect 是否进入 ordinary Repair 由 host 管理决定；遗漏既有 planning obligation 必须以 `PLANNING_ESCAPE` 回到 F10。

如果 host 不提供这些命名技能或模板，遵守其等价 formal contract；不得自行发明角色、文件名或自动派发。

## 完成与停止

任一 planning node 完成时报告：role、phase/node、terminal、source/candidate identities、`PROVEN/INFERENCE/UNKNOWN/CONFLICT`、completed outputs、coverage、pending decisions、protected state、`currentNode`、`firstUnfinishedAction` 与未执行的后续工作。

只有 F8 全部 axis 有证据、Story capacity PASS、final planning 获得明确用户批准，才能输出 `READY`。否则输出 `NOT_READY` 或 `BLOCKED` 及最小恢复条件。

完成 handoff 后停止。不要因为用户说“把它做完”、上下文压力、文档很长或 Review 已发生而实施、派发、合并或降低 oracle。
