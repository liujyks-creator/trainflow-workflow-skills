# 通用 Workflow Skills

一组以 `SKILL.md` 为入口的通用 Agent 工作流技能，以及可人工传递的 Writer、Repair、Reviewer 提示词模板。技能不依赖 TrainFlow 产品代码、安装器或专用运行时；Codex 及其他能够加载目录式指令的 Agent 框架均可使用，具体目录约定由宿主框架决定。

> [!WARNING]
> 本仓库目前是测试版和实验性工作流，不能保证安全、正确或适用于任何项目。技能或提示词可能生成错误修改、覆盖文件、破坏 Git 状态、丢失数据，甚至损毁项目。使用前必须自行备份，在隔离分支或工作树中运行，并人工 Review 所有变更和命令。使用者自行承担全部风险。

## 内容

- `skills/bmad-method/`：从 Discovery、产品、UX、Architecture、Epic/Story 和证据合同推进到 implementation readiness，也支持 Planning Review 与 Correct Course。
- `skills/superpowers/test-driven-development/`：行为变更与缺陷修复的测试驱动方法。
- `skills/superpowers/systematic-debugging/`：从可复现证据追踪根因的系统化调试方法。
- `skills/superpowers/verification-before-completion/`：在完成、提交或推送声明前建立 claim-to-evidence gate。
- `skills/superpowers/reviewing-code/`：独立候选审查及获授权后的机械集成。
- `skills/superpowers/receiving-code-review/`：核对审查发现并实施准确修复。
- `codex/AGENTS.md`：Codex 用户级自定义指令备份。
- `skills/design-md/`：创建和维护设计系统与 `DESIGN.md` 的方法。
- `MAIN_CONTROL_RESTART_PROMPT_TEMPLATE.md`：主管理与跨会话恢复模板。
- `DEV_STORY_PROMPT_TEMPLATE.md`：Writer 与 Repair 模板。
- `CODE_REVIEW_PROMPT_TEMPLATE.md`：Reviewer 与 re-Reviewer 模板。
- `docs/`：历史项目环境资料，不属于可安装的通用技能包。

## 安装与调用

每个包含 `SKILL.md` 的叶子目录都是一个可独立安装的技能包。安装时应保留该目录内的相对文件结构：

- Codex：把需要的叶子技能目录复制到用户技能目录，例如将 `skills/bmad-method/` 安装为 `~/.codex/skills/bmad-method/`，并将需要的 `skills/superpowers/*/` 叶子目录分别安装到 `~/.codex/skills/`。
- 其他 Agent 框架：将对应叶子目录导入该框架的 skills、rules 或 instructions 目录，并让框架以其中的 `SKILL.md` 为入口。若框架使用不同的元数据格式，可增加宿主侧适配，但不要改写技能的承重合同。
- Codex 自定义指令：`codex/AGENTS.md` 对应 `~/.codex/AGENTS.md`（Windows 为 `%USERPROFILE%/.codex/AGENTS.md`）。恢复前保留原文件，并核对个人规则后合并或替换；它不作为本仓库根目录的项目治理文件。
- 三个根目录模板不是自动执行器；请填写完整后，人工传递给对应角色或会话。

仓库根目录不提供项目级 `AGENTS.md`。具体项目的治理、产品事实、路径、权限和验证要求应由使用方项目自行定义，不能由这个通用技能包替代。

## 使用边界

- 这些技能不能替代人工判断、代码 Review、备份或真实验证。
- 技能是方法性指令，不能覆盖宿主 Agent 的系统规则、项目治理、用户授权或安全边界。
- 不要在没有备份的唯一项目副本上试运行。
- 不要把技能输出、测试结果或模型声明直接视为安全证明。
- 执行文件修改、Git、部署、设备或外部系统操作前，应检查具体命令与作用范围。

## 著作权与许可

Copyright (c) 2026. All rights reserved.

本仓库公开仅用于查看。仓库未提供任何开源许可证，也未授予复制、修改、分发、再发布、商业使用、创建衍生作品或再许可的权利。除适用法律明确允许的情形外，任何使用均须事先取得著作权人的书面许可。
