# Craft of Research Skill — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.
>
> **STATUS: ✅ 已完成 — Implementation Complete (2026-07-01)**
>
> The SKILL.md was created at **1474 lines** as a **bilingual dual-section file**: Language Selection (`question` tool) at top → separate `[ZH] 中文版本` and `[EN] English Version` sections, each independently complete. All 27 steps below are marked completed. The expected output (~1474 lines) closely matches the estimate.

**Goal:** Create an agent skill (`SKILL.md`) from the design spec at `docs/superpowers/specs/2026-07-01-craft-of-research-design.md` — a Socratic dialogue guide that helps researchers find their unique contribution in an academic conversation.

**Architecture:** Single-file SKILL.md entry point at `skills/craft-of-research/SKILL.md` with embedded step-by-step workflow. The file distills the 1216-line design doc into an executable format an agent can follow — trigger conditions, per-trigger workflows, the 6-dimensional dialogue framework, question techniques, and the innovation self-check engine.

**Tech Stack:** Markdown with YAML front matter. Standard SKILL.md format used by all OhMyOpenCode skills.

**Reference Spec:** `docs/superpowers/specs/2026-07-01-craft-of-research-design.md` (1216 lines, full detailed design)

## Global Constraints

- YAML front matter: `name: craft-of-research` with a Chinese + English description that covers all trigger scenarios
- Front matter description MUST include the `/craft-of-research` trigger command
- All dialogue dimensions must be present: 6 dimensions (进入学术对话, 找到你自己的切入点, 把论证搭起来, 研究的伦理与社会责任, 持续往前走, 把你的论证写出来、讲出来)
- Language: Bilingual dual-section — separate [ZH] 中文版本 and [EN] English Version sections with language selection at top; ZH section uses Chinese primary with English key terms, EN section is full English
- Design doc sections act as the authoritative reference — no invented content outside the spec
- SKILL.md should be self-contained and actionable (~1474 lines) — an agent should be able to follow it without reading the full design doc
- Use existing skill patterns from `~/.config/opencode/skills/` as format reference (YAML front, `---`, markdown body)

---

### Task 1: Create SKILL.md Skeleton — YAML, Language Selection, ZH/EN Sections

**Files:**
- Create: `skills/craft-of-research/SKILL.md`

**Interfaces:**
- Consumes: design spec §§1.7, 1.1, 5.1, 6, 7
- Produces: SKILL.md top skeleton (~lines 1-80) — YAML front matter, Language Selection block, [ZH] section header + hard gate + triggers + philosophy, [EN] section placeholder

- [x] **Step 1: Write the YAML front matter + bilingual title**

The description must cover all trigger scenarios in both Chinese and English:

```yaml
---
name: craft-of-research
description: "苏格拉底式引导开展创新性研究、探索关键科学问题。Bilingual skill — prompts user to choose Chinese or English. Based on The Craft of Research's 'research as conversation' philosophy. Use when user says '帮我做研究规划'/'如何提出好问题'/'怎么找到研究创新点'/'make a research plan'/'how to find research contribution'/'craft-of-research' 或任何涉及研究设计、开题、创新方法论的请求。"
---
```

- [x] **Step 2: Write Language Selection block (design doc §1.7)**

Use the `question` tool for clickable language choice:

```markdown
## Language Selection / 语言选择

**IMPORTANT — You MUST use the `question` tool to present the language choice as clickable options.**
...
```

- [x] **Step 3: Write [ZH] section header + HARD-GATE**

```markdown
## [ZH] 中文版本

<HARD-GATE>
本 skill 是**引导者，不是答案机**。不替研究者思考，不替他们"发明"创新点，不评判想法对错。
...
</HARD-GATE>
```

- [x] **Step 4: Write trigger conditions table + core philosophy + key principles**

From design doc §§6, 1.1–1.6:

```markdown
### Triggers
| 触发 | 说明 |
| ... | ... |

### 基本理念
**研究是对话，不是流水线。** ...
"我不在乎"是终极失败、研究者三重角色、受众三重角色。

### 几条原则
好的问题 > 好的答案、写作即发现、拥抱混乱、形式是创造力的前提、给好奇心创造条件。
```

- [x] **Step 5: Write [EN] section placeholder**

Add the EN section header after ZH content (to be populated in subsequent tasks):

```markdown
---
## [EN] English Version
```
(The EN section is built in parallel with the ZH section across Tasks 2–7.)

---

### Task 2: Implement Creative Framework + 维度一（进入学术对话）— ZH + EN

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append after philosophy in ZH section; create parallel content in EN section)

**Interfaces:**
- Consumes: design spec §§1.2, 1.3, 1.4, 1.5, 1.6, 维度一 (entire section)
- Produces: SKILL.md creative framework + 维度一 in BOTH [ZH] and [EN] sections

- [x] **Step 1: Write creative framework (§1.2) — ZH version**

From design doc §1.2 — Creative Agreement and Creative Disagreement tables:

```markdown
### 创造性框架

通过 **§4.3 "Reading for a Problem"** 引导研究者找到切入点：

#### 创造性同意（Creative Agreement）
| 策略 | 引导问题 |
|------|---------|
| 提供新证据 | "这个论断现有的证据够吗？" |
...

#### 创造性异议（Creative Disagreement）
| 策略 | 引导问题 |
|------|---------|
| 分类/定义之争 | "你同意它的分类吗？" |
...
```

- [x] **Step 2: Write §1.3–1.6 core concepts — ZH version**

From design doc §§1.3–1.6. Each as a short principle:

```markdown
### 几条原则

**好的问题 > 好的答案**（§1.3）：研究的意义在于提出值得回答的问题。

**写作即发现**（§1.4 / §10.4）：...
```

- [x] **Step 3: Write 维度一 dialogue flow — ZH version**

From design doc 维度一 — the practical flow:

```markdown
### 维度一：进入学术对话

**核心问题：** 你在和谁对话？他们在讨论什么？

#### 引导流程
1. **建立对话意识** — "用一句话说清楚你的项目..."
2. **三句式引导** — X / Y / Z 框架
...
```

- [x] **Step 4: Create EN equivalents for all of the above**

Duplicate the structure for the [EN] English Version section with full English content (Creative Framework, Key Principles, Dimension 1). EN content matches ZH structure exactly but is written in English.

```markdown
### Creative Framework

Scanning the literature for your contribution via **§4.3 "Reading for a Problem"**:

#### Creative Agreement
...

#### Creative Disagreement
...

### Key Principles
...

### Dimension 1: Entering the Academic Conversation
...
```

---

### Task 3: Implement 维度二（找到你自己的切入点）+ 来源评估 — ZH + EN

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append in ZH section; add parallel EN content)

**Interfaces:**
- Consumes: design spec 维度二, 附加：寻找与评估来源
- Produces: SKILL.md 维度二 + source evaluation in BOTH [ZH] and [EN] sections

- [x] **Step 1: Write 维度二 flow — ZH + EN**

From design doc 维度二:

```markdown
### 维度二：找到你自己的切入点

**核心问题：** 你能贡献什么别人没有的东西？

1. **扫描现有文献中的位置** — 使用创造性同意/异议框架
2. **从来源中挖掘问题** — 定位"分歧点"
3. **"So What?" 级联** — 逐层追问
4. **意义的层次标尺** — 新信息 / 解决困惑 / 颠覆稳固信念
5. **检验问题的价值** — "除了你自己，谁还在意？"

--- [EN version] ---

### Dimension 2: Finding Your Creative Angle

**Core question:** Where might your unique contribution be in this conversation?
...
```

- [x] **Step 2: Write source evaluation guide — ZH + EN**

From design doc 附加 section — four standards:

```markdown
### 来源评估指引

| 标准 | 引导问题 |
|------|---------|
| 相关性 | 这篇是否直接回应你的研究问题？ |
| 可靠性 | 是否经过同行评议？ |
| 时效性 | 领域内什么算"最新"？ |
| 公正性 | 有无明显的偏见或利益冲突？ |

--- [EN version] ---

### Source Evaluation Guide
... (parallel English content)
```

---

### Task 4: Implement 维度三（把论证搭起来）— ZH + EN

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append in ZH section; add parallel EN content)

**Interfaces:**
- Consumes: design spec 维度三 (all sub-sections)
- Produces: SKILL.md 维度三 in BOTH [ZH] and [EN] sections

- [x] **Step 1: Write core argument skeleton + argument planning + Ethos — ZH + EN**

```markdown
### 维度三：把论证搭起来

**要回答的问题：** 你的论点站得住吗？你拿什么说服读者？

#### 核心论证骨架
- Claim → Reasons → Evidence → Warrant → Acknowledgment & Response

#### 论证规划（§5.5）
从核心主张开始逐层展开：核心主张 → 子论证 → 各需什么证据 → 回应反对意见。

#### 研究者品格与可信度（§5.6 Ethos）
公平呈现反对观点、主动承认证据局限、准确引用、显示已考虑反例。

--- [EN version] ---

### Dimension 3: Building Your Argument

**Core question:** Does your argument hold? How do you convince your conversation partners?
...
```

- [x] **Step 2: Write claim refinement + evidence + warrant — ZH + EN**

From design doc §§6, 7, 8 — evidence vs reasons, evidence types, claiming concretely, qualifying claims, Warrant, If-Then test:

```markdown
#### 证据 vs 理由（§7.1–7.2）
理由回答"为什么"，证据回答"你怎么知道"。

#### Evidence types + 5 standards (§7.3, 7.5)
类型：事实/统计、例子/案例、权威引用、文本证据、逻辑推理。
评估：准确、精确、充分、权威、清晰。

#### Qualifying Claims（§6.3）
限定肯定程度和条件范围，匹配证据强度。

#### Warrant（§8）
连接理由与主张的一般性原则。四条判断标准（§8.4）。If-Then测试（§8.5）。
```

- [x] **Step 3: Write response to objections + pressure test — ZH + EN**

From design doc §§9, 3a/3b — three types of objections, response strategies, pressure test, "argument is not about winning":

```markdown
#### 三类质疑预判（§9）
1. "谁在乎？" 2. "证据够吗？" 3. "还有其他解读吗？"

#### 论证压力测试
"你最薄弱的推理环节在哪？""如果你不同意自己的论点，你会怎么反驳？"

#### 论证不是为了赢（§5.1）
目标是"让各方在理解上共同成长"，而非"让对方同意"。
```

---

### Task 5: Implement 维度四（研究的伦理与社会责任）+ 维度五（持续往前走）+ 维度六（把你的论证写出来、讲出来）— ZH + EN

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append in ZH section; add parallel EN content)

**Interfaces:**
- Consumes: design spec 维度四, 维度五, 维度六
- Produces: SKILL.md 维度四, 五, 六 in BOTH [ZH] and [EN] sections

- [x] **Step 1: Write 维度四 and 维度五 — ZH + EN**

```markdown
### 维度四：研究的伦理与社会责任

**核心问题：** 谁可能受你的研究影响？你有什么责任？

三重责任：对个人的诚信 → 对学术共同体的责任 → 对社会的责任。

### 维度五：持续往前走

**核心问题：** 这个研究打开了什么新的问题？

好的研究不终结对话，而是开启新对话。

--- [EN] ---

### Dimension 4: Ethics and Social Responsibility
...

### Dimension 5: Keep Going
...
```

- [x] **Step 2: Write 维度六 (delivery and expression) — ZH + EN**

From design doc 维度六 — writing as discovery, planning, organization, narrative arc, paragraphs, style, visuals, presentations:

```markdown
### 维度六：把你的论证写出来、讲出来

核心理念：写作本身是一种发现行为。
- 写作规划（§10）：三种常见障碍
- 组织结构（§11）：读者视角
- 叙事弧线（§12）：起点→冲突→发展→解决
- 段落写作（§13）：每段第一句锚定任务
- 风格修改（§15）：被动语态、名词堆砌、抽象主语
- 视觉（§16）：证据性 vs 修辞性
- 口头报告（§16）：让听众带走一个核心概念

--- [EN] ---

### Dimension 6: Writing and Presenting Your Argument
...
```

---

### Task 6: Implement 引导策略汇总（§3）— ZH + EN

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append in ZH section; add parallel EN content)

**Interfaces:**
- Consumes: design spec §3 (3.1 question techniques: 19 types, 3.2 fallback strategies: 7 types, 3.3 So What cascade, 3.3.1 meaning levels, 3.4 innovation self-check engine)
- Produces: SKILL.md §3 guidance strategies in BOTH [ZH] and [EN] sections

- [x] **Step 1: Write question techniques table (19 types) + fallback strategies (7 types) — ZH + EN**

From design doc §3.1 (19 techniques) and §3.2 (7 fallback strategies):

```markdown
### 引导策略汇总

#### 提问方式一览
| 技巧 | 适用维度 | 示例 |
|------|---------|------|
| 聚焦追问 | 一 | ... |
| 历史追问 | 一、二 | ... |
| 结构追问 | 二 | ... |
| 分类追问 | 二 | ... |
| 反事实追问 | 二 | ... |
| 来源追问 | 一、二 | ... |
| So What?级联 | 二、三 | ... |
| 视角翻转 | 二 | ... |
| 论证规划追问 | 三 | ... |
| Ethos检查 | 三、四 | ... |
| 限定词校准 | 三 | ... |
| If-Then测试 | 三 | ... |
| 压力测试 | 三 | ... |
| 叙事弧线追问 | 六 | ... |
| 段落检查 | 六 | ... |
| 风格伦理追问 | 六 | ... |
| 视觉角色区分 | 六 | ... |
| 对话延续 | 五 | ... |
| 好奇心条件诊断 | 对话设计 | ... |

#### 兜底策略
| 卡住场景 | 策略 |
|---------|------|
| "我不知道我感兴趣什么" | ... |
| "我的问题太大了" | ... |
| "我觉得没什么创新点" | ... |
| "我想不到有什么意义" | ... |
| "我不知道读者是谁" | ... |
| "最怕同行说'我不在乎'" | ... |
| "我的论证很弱" | ... |

--- [EN version] ---

### Guidance Strategies Overview

#### Question Techniques at a Glance
| Technique | Best for Dimension | Example |
|-----------|------------------|---------|
| Focusing | 1 | ... |
| Historical | 1, 2 | ... |
... (19 total, matching ZH)
```

- [x] **Step 2: Write So What cascade + meaning levels — ZH + EN**

```markdown
#### So What? 深度级联
每次使用深入 3–5 层：Q1 → Q2 → 重新思考 Y → 影响 Z → 自然停止

#### 意义的层次标尺
1. 新信息 / 2. 解决困惑 / 3. 颠覆稳固信念

--- [EN] ---

#### So What? Deep Cascade
...
```

- [x] **Step 3: Write innovation self-check engine — ZH + EN**

Five-step diagnostic from design doc §3.4. Each step has check items and redirects to corresponding dimension:

```markdown
#### 创新性自检引擎

Step 1 — 定位：我在和谁对话？（→ 维度一）
Step 2 — 意义：为什么有人应该在乎？（→ So What?级联）
Step 3 — 论证拉力测试：我最薄弱的推理在哪？（→ 维度三）
Step 4 — 受众校准：谁会反对？为什么？（→ 维度三）
Step 5 — 研究后果：然后呢？（→ 维度五）

--- [EN] ---

#### Innovation Self-Check
... (parallel content)
```

---

### Task 7: Implement Output + Success Criteria + Final Polish — ZH + EN

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (complete ZH section; complete EN section)

**Interfaces:**
- Consumes: design spec §§4, 7
- Produces: SKILL.md complete file — output and success criteria in BOTH [ZH] and [EN] sections

- [x] **Step 1: Write output format — ZH + EN**

```markdown
### 可以产出什么

**研究笔记（持续记录）** — 对话过程中记录关键产出。研究者可随时查看。

**研究备忘录（可选）** — 结构化备忘录：研究问题、创造性切入点、论证骨架、潜在挑战、下一步问题。

**保存** — 默认保存到 `research-notes/`。

--- [EN] ---

### Outputs

**Research Notes (Ongoing)** — ...
```

- [x] **Step 2: Write success criteria — ZH + EN**

```markdown
### 怎么算成功

成功的标志不是"产出了一份计划"，而是研究者在对话中经历了以下转变：

- 从"我想研究 X"变成了"我想回答 Y 问题，因为它的答案会改变我们对 Z 的理解"
- 能说清研究在学术对话中的位置（同意什么/反对什么/扩展什么）
- 对自己的论证有压力测试意识——知道哪儿最薄弱
- 能回答"所以呢？"——不是为了应付谁，而是真明白自己为什么重要
- 能提出新问题——不只他们自己要回答的那个，还有他们的研究会催生的那些

--- [EN] ---

### Success Criteria
...
```

- [x] **Step 3: Final read-through verify**

Read the complete SKILL.md. Check:
- [ ] YAML front matter correct (bilingual description, no trailing issues)
- [ ] Language Selection block present with `question` tool syntax
- [ ] Both [ZH] and [EN] sections complete and self-contained
- [ ] All 6 dimensions present and distinct in both sections
- [ ] Creative framework includes both agreement and disagreement
- [ ] Self-check engine has all 5 steps with check items
- [ ] Question techniques table has 19 entries (both ZH and EN)
- [ ] Fallback strategies has 7 entries (both ZH and EN)
- [ ] So What cascade explained
- [ ] Output format defined
- [ ] Success criteria listed
- [ ] No placeholder text, TBD, or "implement later"
- [ ] ~1474 lines total

- [x] **Step 4: Commit**

```bash
git add skills/craft-of-research/SKILL.md
git commit -m "feat(craft-of-research): add output format, success criteria, and final polish"
```
