---
name: craft-of-research
description: "苏格拉底式引导开展创新性研究、探索关键科学问题。Bilingual skill — prompts user to choose Chinese or English. Based on The Craft of Research's 'research as conversation' philosophy. Use when user says '帮我做研究规划'/'如何提出好问题'/'怎么找到研究创新点'/'make a research plan'/'how to find research contribution'/'craft-of-research' 或任何涉及研究设计、开题、创新方法论的请求。"
---

# Craft of Research — Bilingual Skill / 双语技能

> Based on *The Craft of Research* (5th Edition), deeply distilled.
>
> Core philosophy: **Research is not an assembly line for collecting facts — it is an invitation into an ongoing conversation.** The best answers do not end a dialogue; they give birth to new questions.

## Language Selection / 语言选择

**IMPORTANT — You MUST use the `question` tool to present the language choice as clickable options (tabs/buttons). Do NOT ask the user to type their answer.**

Use the `question` tool like this:
```
question(questions=[{
  "header": "Language / 语言",
  "question": "请问您希望用中文还是英文交流？/ Would you like to communicate in Chinese or English?",
  "options": [
    {"label": "中文", "description": "使用中文进行对话"},
    {"label": "English", "description": "Converse in English"}
  ]
}])
```

### 🔴 CHECKPOINT — 确认后路由 / Confirm & Route
After the user selects a language:
1. Map: `"中文"`→`SKILL-zh.md`, `"English"`→`SKILL-en.md`
2. 🔴 Load ONLY the mapped file. If missing, guide directly.
3. No selection → default `SKILL-zh.md`, confirm.

Then read the corresponding file:

- **中文** → Read `SKILL-zh.md`.
- **English** → Read `SKILL-en.md`.

### ⚠️ 失败恢复 / Failure Recovery

| 触发条件 | 一线修复 | 兜底 |
|---------|---------|------|
| question无法呈现选项 | 用文字描述选项供选择 | 默认中文 |
| 对应的文件不存在 | 提示该语言 | 直接用核心哲学引导 |
| 用户中途要切换语言 | 换读对应文件 | 当前段落结束再切 |

### 🛑 红线 / Hard Rules

- **Do NOT** skip the `question` tool — always ask first.
- **Do NOT** read both files — load only one.
- **Do NOT** answer for the researcher — be Socratic (see sub-file HARD-GATE).
