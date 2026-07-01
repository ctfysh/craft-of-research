# Craft of Research — 研究引导技能

> 基于 _The Craft of Research_ (5th Edition) 的苏格拉底式研究引导技能。
>
> 核心哲学：**研究不是收集事实的流水线，而是进入一场持续对话的邀请。** 最好的答案不是结束对话，而是催生新的问题。

A Socratic research-guide skill derived from _The Craft of Research_ (5th Edition). **Research is not an assembly line for collecting facts — it is an invitation into an ongoing conversation.** The best answers do not end a dialogue; they give birth to new questions.

---

## 这是什么 / What Is This

这是一个 **AI 引导技能**（skill），不是帮你写论文的工具，而是一个苏格拉底式的对话伙伴。它的工作方式是通过提问帮你自己想清楚：

- 你的研究在跟谁对话？
- 你能贡献什么别人没有的东西？
- 你的论证站得住吗？
- 你的研究打开了什么新问题？

This is a Socratic dialogue skill — not a paper-writing tool, but a thinking partner that asks you questions until you see your own research more clearly. It is designed for OpenCode and compatible AI coding agents.

---

## 六大对话维度 / Six Dialogue Dimensions

| # | 维度 | 核心问题 |
|---|------|---------|
| 一 | **进入学术对话** | 你在和谁对话？他们在讨论什么？ |
| 二 | **找到你自己的切入点** | 你能贡献什么别人没有的东西？ |
| 三 | **把论证搭起来** | 你的论点站得住吗？你拿什么说服读者？ |
| 四 | **研究的伦理与社会责任** | 谁可能受你的研究影响？你有什么责任？ |
| 五 | **持续往前走** | 这个研究打开了什么新问题？ |
| 六 | **把你的论证写出来、讲出来** | 怎么让你的论证对别人有意义？ |

研究者可以在六个维度之间自由切换，没有固定顺序，没有轮次上限。

| # | Dimension | Core Question |
|---|-----------|---------------|
| 1 | **Entering the Academic Conversation** | Who are you talking to, and what are they discussing? |
| 2 | **Finding Your Creative Angle** | What can you contribute that no one else has? |
| 3 | **Building Your Argument** | Does your argument hold? How do you convince your reader? |
| 4 | **Ethics and Social Responsibility** | Who might your research affect, and what are your responsibilities? |
| 5 | **Keep Going** | What new questions does your research open up? |
| 6 | **Writing and Presenting Your Argument** | How do you make your argument meaningful to others? |

---

## 怎么用 / How to Use

### 在 OpenCode 中

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

### Bilingual Support

启动时会通过 `question` 工具让你选择语言：

- **中文** — 中文为主，关键术语辅助英文
- **English** — Full English dialogue

---

## 项目结构 / Project Structure

```
.
├── book/                          # 全书原文 + 插图
│   ├── craft-of-research-5e.md    # 全文 Markdown（~4800 行）
│   └── figures/                   # 29 张插图
├── skills/
│   └── craft-of-research/
│       └── SKILL.md               # 引导技能本体（~1474 行）
├── docs/superpowers/
│   ├── plans/                     # 实现计划
│   └── specs/                     # 设计文档
└── README.md                      # 本文件
```

---

## 来源 / Source

本技能提炼自 **《The Craft of Research》**（第五版，芝加哥大学出版社），作者 Wayne C. Booth、Gregory G. Colomb、Joseph M. Williams、Joseph Bizup 和 William T. FitzGerald。这是学术界最经典的研究方法论之一，四十多年来帮助了无数研究者学会如何提出问题、构建论证、加入学术对话。

This skill is distilled from **_The Craft of Research_** (5th Edition, University of Chicago Press) by Booth, Colomb, Williams, Bizup, and FitzGerald — one of the most widely used guides to academic research and writing ever published.

---

## 许可证 / License

本项目仅用于教育和研究目的。_The Craft of Research_ 的文本内容版权归原作者和芝加哥大学出版社所有。
