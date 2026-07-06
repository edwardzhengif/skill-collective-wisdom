# 多维度视角分析框架 / Multi-Perspective Analysis Framework (`collective-wisdom`)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/Version-1.3.2-blue.svg)](#)
[![Language](https://img.shields.io/badge/Language-中文%20%2F%20English-green.svg)](#)

> **[简体中文](#多维度视角分析框架-collective-wisdom)** | **[English Version](#multi-perspective-analysis-framework-collective-wisdom)**

---

## 多维度视角分析框架 (collective-wisdom)

### 简介

`collective-wisdom` 是一个结构化的大语言模型（LLM）多视角分析与批判性思考框架。它通过明确的系统指令，引导 AI 在面对复杂决策、方案对比、问题诊断、创意脑暴或方案设计时，能够自动从多个相互独立且互补的视角进行剖析，以减少认知偏差和“回声室效应”，帮助用户理清思路。

该框架不仅适用于 IDE 自定义技能（如 Antigravity / Gemini Skill），也可以直接作为通用的 System Prompt 使用。

### 核心设计哲学

1. **诚实的认知多样性**：框架摒弃了“伪造专家面板进行辩论”的戏剧化形式，而是让 AI 诚实地作为单一实体从不同维度进行剖析，保护用户信任。
2. **三区适用性筛查 (Three-Zone Model)**：
   - **绿区**（安全分析）：普通决策、策略、对比和诊断。
   - **黄区**（部分分析+专业转介）：涉及一定专业领域但用户需要思考框架，AI 只分析非专业维度，并明确提示咨询专业人士。
   - **红区**（直接拒绝）：涉及医疗诊断、法律诉讼、具体投资建议、心理危机等，AI 拒绝分析并提供专业求助通道。
3. **动态输出模式**：
   - **标准模式** (Standard Mode)：800-1500 字，深度分析。
   - **对比模式** (Comparison Mode)：500-800 字，使用多维度表格进行 A vs B 对比，包含“预演失效 (Pre-mortem)”分析。
   - **快速模式** (Quick Mode)：200-400 字，快速响应，一目了然。
4. **置信度定量标示**：对每个视角的论点明确标注 High / Medium / Low 置信度并解释原因，避免过度自信。
5. **反确认偏差**：若检测到用户有明显的偏好倾向，框架会特意加强对立面的深度分析以进行压力测试。

---

### 项目目录结构

```text
.
├── SKILL.md                          # 核心技能定义文件 (System Prompt)
├── LICENSE                           # MIT 开源许可证
├── README.md                         # 项目说明文档 (中英双语)
├── CONTRIBUTING.md                   # 贡献指南 (中英双语)
└── reference/
    ├── analysis-patterns.md          # 优秀案例与常见反模式 (必读)
    └── design-rationale.md           # 框架设计考量与版本演进历史
```

* **[SKILL.md](SKILL.md)**: 包含了完整的 YAML Frontmatter 和 IF-THEN 质量控制规则，适合直接导入到支持 Custom Skill 的 AI 工具中。
* **[reference/analysis-patterns.md](reference/analysis-patterns.md)**: 包含决策、诊断、对比、脑暴等多种场景的优秀输出范例，以及 AI 应避免的空洞分析、强行端平、假装专家等反模式。
* **[reference/design-rationale.md](reference/design-rationale.md)**: 阐述了为什么要采用本设计（例如：为什么免去澄清摩擦、为什么把免责声明放在最后、为什么使用 IF-THEN 结构等）。

---

### 如何使用

#### 1. 在 Cursor 中使用
* **作为全局规则/自定义指令**：打开 Cursor 的 `Settings -> Features -> Rules for AI`，将 `SKILL.md` 中 `---` 之后的内容复制进去。
* **作为项目规则**：在项目根目录下创建 `.cursorrules` 文件，并将 `SKILL.md` 的内容粘贴进去，这样 Cursor 的 Chat、Composer 以及 Agent 均会自动遵循该分析框架。

#### 2. 在 Claude 中使用
* **在 Claude Projects 中使用（推荐）**：如果你是 Claude Pro/Team 用户，可以在 Project 中创建一个项目，并在 `Project Instructions` 中粘贴 `SKILL.md` 的内容。这非常适合在项目范围内针对架构抉择和技术选型进行多视角评估。
* **作为自定义指令 (Custom Instructions)**：在 Claude 的个人 Profile 设置中，将提示词粘贴到 `Custom Instructions` 框中，使其成为你的全局默认分析助手。

#### 3. 在 GitHub Copilot / Codex / OpenAI GPTs 中使用
* **GitHub Copilot (.github/copilot-instructions.md)**：你可以在项目根目录下创建 `.github/copilot-instructions.md`，粘贴本框架的内容。Copilot Chat 会在回答项目相关问题时参考这些指令。
* **OpenAI ChatGPT / GPTs**：在 ChatGPT 中创建一个专属 Custom GPT，在 "Instructions" 中填入 `SKILL.md` 的内容。你还可以将 `reference/` 下的文档上传至 Knowledge 中作为检索增强（RAG）。

#### 4. 作为 Antigravity / Gemini IDE 技能导入
将此项目克隆或复制到你的自定义技能目录（例如全局配置路径 `~/.gemini/config/skills/` 或项目根目录 `.agents/skills/`）：
```bash
git clone https://github.com/edwardzhengif/skill-collective-wisdom.git ~/.gemini/config/skills/prompt-collective-wisdom
```
IDE 将自动识别 `SKILL.md` 并注册为名为 `collective-wisdom` 的技能。

#### 5. 通用 System Prompt
打开 `SKILL.md`，复制 `---` 之后的所有正文内容，粘贴到任意大语言模型客户端的系统提示词或自定义指令中即可。

---

## Multi-Perspective Analysis Framework (collective-wisdom)

### Introduction

`collective-wisdom` is a structured multi-perspective analysis and critical thinking framework for Large Language Models (LLMs). Through highly explicit system directives, it guides the AI to analyze complex decisions, comparisons, diagnoses, brainstorming sessions, or solution designs from multiple independent and complementary angles. This helps reduce cognitive biases and the "echo chamber effect," enabling users to clarify their thinking processes.

This framework is highly compatible with IDE Custom Skills (such as Antigravity / Gemini Skill) and can also be used directly as a generic System Prompt.

### Core Design Philosophy

1. **Honest Cognitive Diversity**: The framework avoids the theatrical pretense of a "simulated expert panel debate." Instead, the AI honestly analyzes the problem as a single entity from different dimensions, maintaining user trust.
2. **Three-Zone Applicability Model**:
   - **Green Zone** (Full Analysis): Standard decisions, strategy, comparisons, and diagnoses.
   - **Yellow Zone** (Partial Analysis + Referral): Bordering professional domains where the user wants a thinking framework. The AI analyzes non-professional dimensions and recommends consulting qualified professionals.
   - **Red Zone** (Rejection): Specific medical, legal, financial advice, or crises. The AI rejects the analysis and immediately provides professional hotline resources.
3. **Dynamic Output Modes**:
   - **Standard Mode**: 800-1500 words, in-depth analysis.
   - **Comparison Mode**: 500-800 words, utilizing a multi-dimensional table for A vs B comparisons, featuring a "Pre-mortem" failure analysis.
   - **Quick Mode**: 200-400 words, concise and scannable.
4. **Explicit Confidence Ratings**: Every viewpoint specifies a High / Medium / Low confidence rating with justification, preventing false certainty.
5. **Mitigating Confirmation Bias**: If the user shows a preference towards one option, the framework intentionally strengthens the depth of the opposing perspective to stress-test the preference.

---

### Folder Structure

```text
.
├── SKILL.md                          # Core Skill Definition (System Prompt)
├── LICENSE                           # MIT License
├── README.md                         # Project Readme (Bilingual)
├── CONTRIBUTING.md                   # Contributing Guide (Bilingual)
└── reference/
    ├── analysis-patterns.md          # Good examples & anti-patterns (Must read)
    └── design-rationale.md           # Rationale behind decisions & history
```

* **[SKILL.md](SKILL.md)**: Contains the full YAML Frontmatter and IF-THEN quality verification rules, ready for integration into Custom Skill-supported AI systems.
* **[reference/analysis-patterns.md](reference/analysis-patterns.md)**: Features high-quality output templates for decision-making, diagnosis, comparison, and brainstorming, alongside anti-patterns to avoid (e.g., empty analysis, forced balance, pretending expertise).
* **[reference/design-rationale.md](reference/design-rationale.md)**: Explains the design decisions (e.g., why clarification friction is optional, why the disclaimer is appended at the end, and why IF-THEN rules are preferred over standard checklists).

---

### How to Use

#### 1. In Cursor
* **Global Rules**: Go to Cursor's `Settings -> Features -> Rules for AI`, and paste the content of `SKILL.md` (excluding YAML frontmatter).
* **Project Rules (.cursorrules)**: Create a `.cursorrules` file in the root of your project, and paste the content of `SKILL.md` there. Cursor Chat, Composer, and Agent will automatically adopt this multi-perspective analysis framework.

#### 2. In Claude
* **Claude Projects (Recommended)**: For Claude Pro/Team users, create a Project and paste the text of `SKILL.md` into the `Project Instructions`. This is perfect for technical stack choices, architecture design, and decision support within a repository.
* **Custom Instructions**: Paste the prompt into the `Custom Instructions` section in your Claude Profile Settings to use it as a global default analysis assistant.

#### 3. In GitHub Copilot / Codex / OpenAI GPTs
* **Copilot Instructions**: Create a `.github/copilot-instructions.md` file in your repository root, and paste the framework guidelines. Copilot Chat will read and apply it for repo-level queries.
* **OpenAI ChatGPT / Custom GPTs**: Create a custom GPT in ChatGPT, and paste the `SKILL.md` content into its "Instructions". You can also upload the files in the `reference/` directory to the GPT's Knowledge base to provide additional context.

#### 4. Import as an Antigravity / Gemini IDE Skill
Clone or copy this repository into your custom skills directory (e.g., global path `~/.gemini/config/skills/` or workspace-scoped path `.agents/skills/`):
```bash
git clone https://github.com/edwardzhengif/skill-collective-wisdom.git ~/.gemini/config/skills/prompt-collective-wisdom
```
The IDE will automatically discover `SKILL.md` and load it as a skill named `collective-wisdom`.

#### 5. Generic System Prompt
Copy the text in `SKILL.md` (below the `---` frontmatter delimiter) and paste it into the system prompt or custom instructions panel of any LLM client (Web UI, API playground, etc.).

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
