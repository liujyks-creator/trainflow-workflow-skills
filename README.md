# TrainFlow Workflow Skills

TrainFlow 项目使用的本地 BMAD、TDD、系统化调试、完成前验证、设计文档技能，以及人工 Writer / Repair / Reviewer 交付模板。

> [!WARNING]
> 本项目目前是测试版和实验性工作流，不能保证安全、正确或适用于任何项目。技能或提示词可能生成错误修改、覆盖文件、破坏 Git 状态、丢失数据，甚至损毁项目。使用前必须自行备份，在隔离分支或工作树中运行，并人工 Review 所有变更和命令。使用者自行承担全部风险。

## 内容

- `skills/bmad-method/`：产品、架构、Story、readiness 与 Correct Course。
- `skills/superpowers/`：项目获准使用的 TDD、系统化调试和完成前验证方法。
- `skills/design-md/`：设计系统与 `DESIGN.md` 方法。
- `AGENTS.md`：TrainFlow 项目治理与使用边界。
- `MAIN_CONTROL_RESTART_PROMPT_TEMPLATE.md`：主管理提示词模板。
- `DEV_STORY_PROMPT_TEMPLATE.md`：Writer 与 Repair 模板。
- `CODE_REVIEW_PROMPT_TEMPLATE.md`：Reviewer 与 re-Reviewer 模板。
- `docs/`：安装、环境与新电脑设置说明。

## 使用边界

- 这些技能不能替代人工判断、代码 Review、备份或真实验证。
- 不要在没有备份的唯一项目副本上试运行。
- 不要把技能输出、测试结果或模型声明直接视为安全证明。
- 执行文件修改、Git、部署、设备或外部系统操作前，应检查具体命令与作用范围。

## 著作权与许可

Copyright (c) 2026. All rights reserved.

本仓库公开仅用于查看。仓库未提供任何开源许可证，也未授予复制、修改、分发、再发布、商业使用、创建衍生作品或再许可的权利。除适用法律明确允许的情形外，任何使用均须事先取得著作权人的书面许可。
