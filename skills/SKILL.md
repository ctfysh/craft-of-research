---
name: craft-of-research
description: "苏格拉底式引导开展创新性研究、探索关键科学问题。Bilingual skill — prompts user to choose Chinese or English. Based on The Craft of Research's 'research as conversation' philosophy. Use when user says '帮我做研究规划'/'如何提出好问题'/'怎么找到研究创新点'/'make a research plan'/'how to find research contribution'/'craft-of-research' 或任何涉及研究设计、开题、创新方法论的请求。"
---

# Craft of Research — Bilingual Skill / 双语技能

> Based on *The Craft of Research* (5th Edition), deeply distilled.
>
> Core philosophy: **Research is not an assembly line for collecting facts — it is an invitation into an ongoing conversation.** The best answers do not end a dialogue; they give birth to new questions.

## Language Selection / 语言选择

**Step 1 — Auto-detect from the user's trigger text.**

Analyze the user's original message for language signals:
- Contains Chinese characters (的/了/吗/呢/做/想/帮/请...) → **中文** → Read `SKILL-zh.md`
- All-English (no CJK characters, English words/phrases) → **English** → Read `SKILL-en.md`
- Triggers `/craft-of-research` in English context → **English**
- Triggers `/craft-of-research` in Chinese context → **中文**

**Step 2 — Only if ambiguous, ask via `question` tool.**

Use the `question` tool only when the trigger contains mixed languages or no clear language signal:
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

**Step 3 — Route.**

1. Map: detected/requested language → `SKILL-zh.md` or `SKILL-en.md`
2. 🔴 Load ONLY the mapped file. If missing, guide directly.
3. Default fallback: `SKILL-zh.md`.

### ⚠️ 失败恢复 / Failure Recovery

| 触发条件 | 一线修复 | 兜底 |
|---------|---------|------|
| 语言检测不确定 | 用 question 工具让选择 | 默认中文 |
| 对应的文件不存在 | 提示该语言 | 直接用核心哲学引导 |
| 用户中途要切换语言 | 换读对应文件 | 当前段落结束再切 |

### 🛑 红线 / Hard Rules

- **Do NOT** always ask language — auto-detect first, ask only if ambiguous.
- **Do NOT** read both files — load only one.
- **Do NOT** answer for the researcher — be Socratic (see sub-file HARD-GATE).
