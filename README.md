# Craft of Research

> A Socratic research-guide skill distilled from _The Craft of Research_ (5th Edition).

---

**Read this document in:**

- [**English**](#english)
- [**中文**](#中文)

---

<!-- ================================================================== -->
<!-- ENGLISH                                                                -->
<!-- ================================================================== -->

## <span id="english">English</span>

A Socratic research-guide skill derived from _The Craft of Research_ (5th Edition). **Research is not an assembly line for collecting facts — it is an invitation into an ongoing conversation.** The best answers do not end a dialogue; they give birth to new questions.

### What Is This

This is an AI skill — not a paper-writing tool, but a Socratic thinking partner. It works by asking questions until you see your own research more clearly:

- Who are you talking to, and what are they discussing?
- What can you contribute that no one else has?
- Does your argument hold? How do you convince your reader?
- What new questions does your research open up?

Designed for OpenCode and compatible AI coding agents.

### The Six Dimensions

| # | Dimension | Core Question |
|---|-----------|---------------|
| 1 | **Entering the Academic Conversation** | Who are you talking to, and what are they discussing? |
| 2 | **Finding Your Creative Angle** | What can you contribute that no one else has? |
| 3 | **Building Your Argument** | Does your argument hold? How do you convince your reader? |
| 4 | **Ethics and Social Responsibility** | Who might your research affect, and what are your responsibilities? |
| 5 | **Keep Going** | What new questions does your research open up? |
| 6 | **Writing and Presenting Your Argument** | How do you make your argument meaningful to others? |

Researchers can switch freely between dimensions — no fixed order, no turn limit.

### How to Use

**In OpenCode:**

```
/craft-of-research
```

Or describe your need directly. The skill activates automatically on trigger phrases:

| Trigger | What happens |
|---------|-------------|
| "I want to do research but don't know where to start" | Full dialogue, beginning at dimension 1 |
| "How do I formulate a good research question?" | Focus on dimensions 1 and 2 |
| "What's innovative about my research?" | Focus on dimension 2 |
| "Help me clarify my argument" | Focus on dimension 3 |
| "Is my research meaningful?" | "So What?" deep cascade |
| "Are there ethical issues in my research?" | Focus on dimension 4 |
| "What can I do next?" | Focus on dimension 5 |
| "I'm stuck on writing / presenting" | Focus on dimension 6 |

**Language selection:** On startup, the skill uses the `question` tool to ask whether you prefer English or Chinese.

### Project Structure

```
.
├── book/                          # Full book text + figures
│   ├── craft-of-research-5e.md    # Full text as Markdown (~4800 lines)
│   └── figures/                   # 29 images
├── skills/
│   └── craft-of-research/
│       └── SKILL.md               # The skill itself (~1474 lines)
├── docs/superpowers/
│   ├── plans/                     # Implementation plans
│   └── specs/                     # Design specifications
└── README.md                      # This file
```

### Source

This skill is distilled from **_The Craft of Research_** (5th Edition, University of Chicago Press) by Wayne C. Booth, Gregory G. Colomb, Joseph M. Williams, Joseph Bizup, and William T. FitzGerald — one of the most widely used guides to academic research and writing ever published.

### License

This project is for educational and research purposes only. The text of _The Craft of Research_ is copyright by the authors and the University of Chicago Press.

---

<!-- ================================================================== -->
<!-- 中文                                                                   -->
<!-- ================================================================== -->

## <span id="中文">中文</span>

基于 _The Craft of Research_（第五版）的苏格拉底式研究引导技能。**研究不是收集事实的流水线，而是进入一场持续对话的邀请。** 最好的答案不是结束对话，而是催生新的问题。

### 这是什么

这是一个 AI 引导技能（skill），不是帮你写论文的工具，而是一个苏格拉底式的对话伙伴。它的工作方式是通过提问帮你自己想清楚：

- 你在和谁对话？他们在讨论什么？
- 你能贡献什么别人没有的东西？
- 你的论点站得住吗？你拿什么说服读者？
- 你的研究打开了什么新问题？

适用于 OpenCode 及兼容的 AI 编程工具。

### 六大对话维度

| # | 维度 | 核心问题 |
|---|------|---------|
| 一 | **进入学术对话** | 你在和谁对话？他们在讨论什么？ |
| 二 | **找到你自己的切入点** | 你能贡献什么别人没有的东西？ |
| 三 | **把论证搭起来** | 你的论点站得住吗？你拿什么说服读者？ |
| 四 | **研究的伦理与社会责任** | 谁可能受你的研究影响？你有什么责任？ |
| 五 | **持续往前走** | 这个研究打开了什么新问题？ |
| 六 | **把你的论证写出来、讲出来** | 怎么让你的论证对别人有意义？ |

研究者可以在六个维度之间自由切换，没有固定顺序，没有轮次上限。

### 怎么用

**在 OpenCode 中：**

```
/craft-of-research
```

或直接描述你的需求——技能会根据触发词自动激活：

| 触发 | 效果 |
|------|------|
| "我要做研究但不知道从何下手" | 完整对话，从维度一开始 |
| "如何提出好的研究问题" | 聚焦维度一、二 |
| "我的研究有什么创新点" | 聚焦维度二 |
| "帮我理清论证" | 聚焦维度三 |
| "我的研究有没有价值" | "So What?" 深度级联 |
| "我的研究有没有伦理问题" | 聚焦维度四 |
| "接下来还可以做什么" | 聚焦维度五 |
| "我的表达/写作卡住了" | 聚焦维度六 |

**语言选择：** 启动时 skill 会通过 `question` 工具让你选择中文或英文。

### 项目结构

```
.
├── book/                          # 全书原文 + 插图
│   ├── craft-of-research-5e.md    # 全文 Markdown（约 4800 行）
│   └── figures/                   # 29 张插图
├── skills/
│   └── craft-of-research/
│       └── SKILL.md               # 引导技能本体（约 1474 行）
├── docs/superpowers/
│   ├── plans/                     # 实现计划
│   └── specs/                     # 设计文档
└── README.md                      # 本文件
```

### 来源

本技能提炼自 **《The Craft of Research》**（第五版，芝加哥大学出版社），作者 Wayne C. Booth、Gregory G. Colomb、Joseph M. Williams、Joseph Bizup 和 William T. FitzGerald。这是学术界最经典的研究方法论之一，四十多年来帮助了无数研究者学会如何提出问题、构建论证、加入学术对话。

### 许可证

本项目仅用于教育和研究目的。《The Craft of Research》的文本内容版权归原作者和芝加哥大学出版社所有。
