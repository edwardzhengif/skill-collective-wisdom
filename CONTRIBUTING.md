# 贡献指南 / Contributing Guide

> **[简体中文](#贡献指南)** | **[English Version](#contributing-guide-english)**

---

## 贡献指南

感谢你对 `collective-wisdom` 项目的关注！我们欢迎各种形式的贡献，包括报告问题、完善提示词规则、补充案例研究以及优化参考文档。

### 参与方式

1. **报告问题 (Issues)**：如果你在使用过程中发现 AI 输出不佳、违反规则或者有更佳的提示策略，请提交一个 Issue，并附带输入问题和 AI 输出结果。
2. **提交改进 (Pull Requests)**：如果你直接修改了代码或文档，欢迎提交 PR！

### 核心准则

在修改 `SKILL.md` 或 `reference/` 目录下的文档时，请务必遵守以下原则：

* **避免伪专家化**：不要编写引导 AI 扮演特定“虚拟专家角色”的指令，要让 AI 诚实地以一个整体从不同视角剖析问题。
* **安全性至上**：三区模型（绿区、黄区、红区）是安全红线，任何修改不能削弱对医疗、法律、财务、心理危机的拦截与转介。
* **IF-THEN 规则格式**：在 `SKILL.md` 的 Quality Rules 中添加规则时，请尽量使用明确的 `IF [触发条件] -> THEN [应对动作]` 格式，大语言模型对这种条件指令的遵循程度远高于普通清单。
* **同步更新文档**：如果修改了 `SKILL.md` 的机制，请在 `reference/design-rationale.md` 的版本历史中记录变更，并提供相关的原理说明；若新增了场景，请在 `reference/analysis-patterns.md` 中添加正反例。

### 提交 Pull Request 流程

1. **Fork** 本仓库并克隆到本地。
2. **创建分支**：`git checkout -b feature/your-feature-name`。
3. **本地测试**：将你修改后的 `SKILL.md` 导入到你的 IDE（如 Antigravity）中，运行几轮复杂的测试，确保没有引入回归问题，AI 输出依旧结构清晰、置信度准确。
4. **提交 commit**：我们建议使用 [Conventional Commits](https://www.conventionalcommits.org/) 规范（例如：`docs: update readme`，`feat: add new analysis perspective`）。
5. **推送分支**：`git push origin feature/your-feature-name`。
6. **创建 Pull Request**，并描述你的修改内容和测试结果。

---

## Contributing Guide (English)

Thank you for your interest in contributing to `collective-wisdom`! We welcome all contributions, including bug reports, rule enhancements, case study expansions, and documentation improvements.

### How to Contribute

1. **Submit Issues**: If you experience poor AI outputs, broken rules, or have suggestions for better prompting strategies, please create an Issue. Include your input prompt and the resulting AI response if possible.
2. **Submit Pull Requests (PRs)**: If you've directly made improvements to the prompts or docs, feel free to submit a PR!

### Core Principles

When modifying `SKILL.md` or files inside the `reference/` directory, please adhere to these guidelines:

* **No Pseudo-Experts**: Do not instruct the AI to pretend to be specific virtual personas/experts. Keep the analysis honest and unified.
* **Safety First**: The Three-Zone Model (Green, Yellow, Red) is our safety baseline. No modifications should weaken the filtering or referral system for medical, legal, financial, or mental health crises.
* **IF-THEN Format for Rules**: When adding validation rules to the Quality Rules in `SKILL.md`, use the explicit `IF [condition] -> THEN [action]` format. LLMs follow conditional structures much better than generic checklists.
* **Synchronize Documentation**: If you modify the core mechanics in `SKILL.md`, record the change in the version history of `reference/design-rationale.md` and explain the rationale. If you introduce a new feature, update `reference/analysis-patterns.md` with good examples and anti-patterns.

### Pull Request Process

1. **Fork** this repository and clone it locally.
2. **Create a branch**: `git checkout -b feature/your-feature-name`.
3. **Local Testing**: Import your modified `SKILL.md` into your IDE (e.g., Antigravity) and run a few complex queries. Verify that outputs are well-structured, confidence scores are realistic, and no regression is introduced.
4. **Commit changes**: We recommend using [Conventional Commits](https://www.conventionalcommits.org/) (e.g., `docs: update readme`, `feat: add new analysis perspective`).
5. **Push branch**: `git push origin feature/your-feature-name`.
6. **Open a Pull Request** describing your changes and test results.
