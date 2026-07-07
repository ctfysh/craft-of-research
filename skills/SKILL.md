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
}]
```

After the user selects a language, read the corresponding file:

- **中文** → Read `SKILL-zh.md` in the same directory. Converse in Chinese, using English for key terms as noted.
- **English** → Read `SKILL-en.md` in the same directory. Converse entirely in English.
- **No selection** → Default to `SKILL-zh.md` (中文).

Do NOT read both files. Load only the one matching the user's language choice.
