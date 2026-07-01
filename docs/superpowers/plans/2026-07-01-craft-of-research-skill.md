# Craft of Research Skill — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create an agent skill (`SKILL.md`) from the design spec at `docs/superpowers/specs/2026-07-01-craft-of-research-design.md` — a Socratic dialogue guide that helps researchers find their unique contribution in an academic conversation.

**Architecture:** Single-file SKILL.md entry point at `skills/craft-of-research/SKILL.md` with embedded step-by-step workflow. The file distills the 1216-line design doc into an executable format an agent can follow — trigger conditions, per-trigger workflows, the 6-dimensional dialogue framework, question techniques, and the innovation self-check engine.

**Tech Stack:** Markdown with YAML front matter. Standard SKILL.md format used by all OhMyOpenCode skills.

**Reference Spec:** `docs/superpowers/specs/2026-07-01-craft-of-research-design.md` (1216 lines, full detailed design)

## Global Constraints

- YAML front matter: `name: craft-of-research` with a Chinese + English description that covers all trigger scenarios
- Front matter description MUST include the `/craft-of-research` trigger command
- All dialogue dimensions must be present: 6 dimensions (进入学术对话, 找到创造性切入点, 构建论证, 伦理, 演进, 交付)
- Language: Chinese primary, English for key terms (must preserve bilingual terminology from spec)
- Design doc sections act as the authoritative reference — no invented content outside the spec
- SKILL.md should be self-contained and actionable (~300-500 lines) — an agent should be able to follow it without reading the full design doc
- Use existing skill patterns from `~/.config/opencode/skills/` as format reference (YAML front, `---`, markdown body)

---

### Task 1: Create SKILL.md Skeleton — Header, Philosophy, Hard Gate

**Files:**
- Create: `skills/craft-of-research/SKILL.md`

**Interfaces:**
- Consumes: design spec §§1, 5.1, 6, 7
- Produces: SKILL.md lines 1-~60 (YAML front matter, description, hard gate, core philosophy table, trigger list)

- [ ] **Step 1: Write the YAML front matter + description**

The description must cover all trigger scenarios. Format from design doc §0 (existing YAML header at line 1-3):

```yaml
---
name: craft-of-research
description: "苏格拉底式引导开展创新性研究、探索关键科学问题。基于《The Craft of Research》的'研究即对话'哲学，通过深度对话帮助研究者找到自己在学术对话中的独特贡献——无论是通过创造性同意/异议、提出新问题，还是重构旧问题。Use when user says '帮我做研究规划'/'如何提出好问题'/'怎么找到研究创新点'/'craft-of-research' 或任何涉及研究设计、开题、创新方法论的请求。对话语言：中文为主，关键术语辅助英文。"
---
```

- [ ] **Step 2: Write the hard gate**

From design doc §1 `<HARD-GATE>` block (lines 12-20):

```markdown
<HARD-GATE>
本 skill 是**引导者，不是解答者**。永远不代替研究者思考，不替他们"发明"创新点，不评价想法对错。

你的工作是帮研究者进入一场与自己、与文献、与学术共同体的真实对话——让他们自己发现什么值得问、什么值得说、什么值得争论。

绝对禁止：代替研究者撰写论文、生成文献综述、搜索文献、评价研究者想法的"正确性"。

对话**不设轮次限制**——研究是持续的过程，随时可以根据理解去改进和深化。
</HARD-GATE>
```

- [ ] **Step 3: Write trigger conditions table**

From design doc §6 — format as a table:

```markdown
## Triggers

| 触发 | 说明 |
|------|------|
| "我要做研究但不知道从何下手" | 完整对话，从维度一开始 |
| "如何提出好的研究问题" | 聚焦维度一、二 |
| "我的研究有什么创新点" | 聚焦维度二 |
| "帮我理清论证" | 聚焦维度三 |
| "我的研究有没有价值" | "So What?" 深度级联 |
| "我的研究有没有伦理问题" | 聚焦维度四 |
| "接下来还可以做什么" | 聚焦维度五 |
| "我的表达/写作卡住了" | 聚焦维度六 |
| "/craft-of-research" | 显式命令 |
```

- [ ] **Step 4: Write core philosophy**

From design doc §1.1 (dialog vs pipeline metaphor, the table). Distill the key insight — "我不在乎" is the ultimate failure, researcher triple role, audience triple role:

```markdown
## 核心理念

**研究是对话，不是流水线。** 你做研究不是"发现真理再报告给受众"，而是进入一个已经进行了几个世纪的对话。

- **"我不在乎"是终极失败** — 最糟糕的回应不是"我不同意"，而是"我不在乎"
- **研究者三重角色**：信息提供者 → 问题解决者 → 知识推进者（目标是角色3）
- **受众三重角色**：取悦我 → 解决实践问题 → 帮助理解更深（学术受众总是角色3）
```

- [ ] **Step 5: Commit**

```bash
git add skills/craft-of-research/SKILL.md
git commit -m "feat(craft-of-research): add skill skeleton with triggers and philosophy"
```

---

### Task 2: Implement 核心创造性框架 + 维度一（进入学术对话）

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append after philosophy)

**Interfaces:**
- Consumes: design spec §§1.2, 1.3, 1.4, 1.5, 1.6, 维度一 (entire section)
- Produces: SKILL.md sections for creative framework + 维度一

- [ ] **Step 1: Write creative framework (§1.2)**

From design doc §1.2 — Creative Agreement and Creative Disagreement tables. Present as actionable checks:

```markdown
## 创造性框架

通过 **§4.3 "Reading for a Problem"** 引导研究者找到切入点：

### 创造性同意（Creative Agreement）
| 策略 | 引导问题 |
|------|---------|
| 提供新证据 | "这个论断现有的证据够吗？" |
| 确认未证实的论断 | "前人假设了什么？你能证明它吗？" |
| 扩展适用范围 | "这个规律在别的领域也成立吗？" |

### 创造性异议（Creative Disagreement）
| 策略 | 引导问题 |
|------|---------|
| 分类/定义之争 | "你同意它的分类吗？" |
| 整体-部分之争 | "部分之间的关系真的如此吗？" |
| 因果之争 | "这是真正的因果关系还是相关？" |
| 历史/发展之争 | "它的演变路径是否被误述了？" |
| 视角之争 | "换个角度看呢？" |
```

- [ ] **Step 2: Write §1.3–1.6 core concepts (concise)**

From design doc §§1.3–1.6. Present each as a short principle with one key quote:

```markdown
## 关键原则

**好的问题 > 好的答案**（§1.3）：研究的意义在于提出值得回答的问题。

**写作即发现**（§1.4 / §10.4）："正是在打草稿时，我们常常体验到研究中最激动人心的时刻之一：我们发现了那些直到将其表达出来才拥有的想法。"

**拥抱混乱**（§1.5 / §18.3）：研究不是线性过程。skill 不设严格的阶段边界，允许随时回环。

**形式是创造力的先决条件**（§1.6 / §18.1）：形式不是创造力的敌人，而是它的条件。

**为好奇心创造条件**（§18.2）：如果研究者卡住，检查：线索不足？受众不明？反馈缺失？
```

- [ ] **Step 3: Write 维度一 dialogue flow**

From design doc 维度一 — extract the practical flow an agent follows:

```markdown
## 维度一：进入学术对话

**核心问题：** 你在和谁对话？他们在讨论什么？

### 引导流程

1. **建立对话意识** — "如果你必须用一句话说清楚你的项目——'我研究 X，因为我想弄明白 Y，从而帮助大家更好地理解 Z'——那会是什么？"
2. **三句式引导** — 帮助研究者填充 X / Y / Z 三个部分。第三部分（"从而…"）说不清是正常的。
3. **"我不在乎"检查** — "如果你在会议上说出你的问题，台下的人会说'我不在乎'吗？为什么？"
4. **阅读方法引导** — 推荐两遍阅读法（第一遍宽厚读，第二遍批判读），并引导从文献中识别论证结构（§4.4）和收集数据（§4.5）

### 引言作为思考框架

Context → Problem（缺口+代价）→ Response 结构。向研究者解释三个步骤，但不要把结构作为"规则"强加，而是作为思考工具。

如果研究者引言太长——用 §14.5 节奏控制原则帮助他们判断目标读者的了解程度，再按需裁剪。

### 结论框架

重申核心主张 → 添加新的意义/应用 → 指向未来。
```

- [ ] **Step 4: Commit**

```bash
git add skills/craft-of-research/SKILL.md
git commit -m "feat(craft-of-research): add creative framework and dimension 1"
```

---

### Task 3: Implement 维度二（找到创造性切入点）+ 附加（来源评估）

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append after 维度一)

**Interfaces:**
- Consumes: design spec 维度二, 附加：寻找与评估来源
- Produces: SKILL.md sections for 维度二 + source evaluation

- [ ] **Step 1: Write 维度二 flow**

From design doc 维度二:

```markdown
## 维度二：找到创造性切入点

**核心问题：** 在这个对话中，你的独特贡献可能在哪里？

### 引导策略

1. **扫描现有文献中的位置** — 使用创造性同意/异议框架扫描可能的切入点
2. **从来源中挖掘问题** — 引导研究者定位"分歧点"：文献中有哪些矛盾或不完整的解释？
3. **"So What?" 级联** — 逐层深入追问，直到研究者自然停止不再需要追问"所以呢"
4. **意义的层次标尺** — 帮助研究者定位贡献层次：新信息 / 解决困惑 / 颠覆稳固信念
5. **检验问题的价值** — "除了你自己，谁还在意这个问题？""如果这个问题被回答了，会改变什么？"
```

- [ ] **Step 2: Write source evaluation guide (concise)**

From design doc 附加 section:

```markdown
## 来源评估指引

当研究者需要评估文献质量时，使用四项标准：

| 标准 | 引导问题 |
|------|---------|
| 相关性 | 这篇是否直接回应你的研究问题？ |
| 可靠性 | 是否经过同行评议？作者是否被认可？ |
| 时效性 | 领域内什么算"最新"？ |
| 公正性 | 有无明显的偏见或利益冲突？ |

**引导："除了这个领域人人都读的标准文献——还有什么不同领域/媒介/时代的来源可能带来新鲜角度？"**
```

- [ ] **Step 3: Commit**

```bash
git add skills/craft-of-research/SKILL.md
git commit -m "feat(craft-of-research): add dimension 2 and source evaluation"
```

---

### Task 4: Implement 维度三（构建有意义的论证）

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append after 维度二)

**Interfaces:**
- Consumes: design spec 维度三 (all sub-sections)
- Produces: SKILL.md sections for 维度三

- [ ] **Step 1: Write core argument skeleton + argument planning + Ethos**

```markdown
## 维度三：构建有意义的论证

**核心问题：** 你的论点成立吗？你用什么说服对话伙伴？

### 核心论证骨架
- "你希望读者最终相信什么？" → Claim
- "你凭什么这么说？" → Reasons
- "每个理由背后，你用什么东西支持？" → Evidence
- "为什么这个理由能支撑这个结论？" → Warrant
- "如果有人拿反例质疑，你怎么应对？" → Acknowledgment & Response

### 论证规划（§5.5）
从核心主张开始逐层展开：核心主张 → 子论证1/2/3 → 各需什么证据 → 回应反对意见 → 指向的意义。

### 研究者品格与可信度（§5.6 Ethos）
建立 Ethos 的策略：公平呈现反对观点、主动承认证据局限、准确引用、措辞尊重、显示已考虑反例。
```

- [ ] **Step 2: Write claim refinement + evidence + warrant**

From design doc §§6, 7, 8:

```markdown
### 证据 vs 理由（§7.1–7.2）
理由回答"为什么"，证据回答"你怎么知道"。混淆两者是研究者最常见的错误。

### 证据类型（§7.3）与证据评估五项标准（§7.5）
类型：事实/统计、例子/案例、权威引用、文本证据、逻辑推理。
评估：准确、精确、充分且有代表性、权威、清晰。

### 主张具体化（§6.1）
阶段：初始感觉 → 识别关键词 → 系词检查 → 范围校准 → 对话定位。

### Qualifying Claims（§6.3）
- 限定肯定程度：强/中/弱主张匹配证据强度
- 限定条件范围：时间、群体、场景、来源

### Warrant（§8）
Warrant 是连接理由与主张的一般性原则。最难的研究挑战的是warrant层面的假设。
- 四条判断标准（§8.4）：读者共享？步骤复杂？可被挑战？非主流？
- If-then测试（§8.5）："接受我的理由→是否必须接受我的主张？"
```

- [ ] **Step 3: Write response to objections + pressure test**

From design doc §§9, 3a/3b:

```markdown
### 三类质疑预判（§9）
1. 关于研究问题（"谁在乎？"）
2. 关于论证可靠性（"证据够吗？"）
3. 关于替代解释（"还有其他解读吗？"）

### 回应策略
让步+限定 / 拒绝 / 反转。优先回应领域内重要替代观点和重要反例。

### 论证压力测试
- "你最薄弱的推理环节在哪？"
- "如果你不同意自己的论点，你会怎么反驳？"

### 论证不是为了赢（§5.1）
研究论证的目标不是"让对方同意"，而是"让各方在理解上共同成长"。
```

- [ ] **Step 4: Commit**

```bash
git add skills/craft-of-research/SKILL.md
git commit -m "feat(craft-of-research): add dimension 3 with full argument framework"
```

---

### Task 5: Implement 维度四（伦理）+ 维度五（演进）+ 维度六（交付）

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append after 维度三)

**Interfaces:**
- Consumes: design spec 维度四, 维度五, 维度六
- Produces: SKILL.md sections for 维度四, 五, 六

- [ ] **Step 1: Write 维度四 and 维度五**

```markdown
## 维度四：研究的伦理与社会责任

**核心问题：** 谁可能受你的研究影响？你有什么责任？

三重责任：对个人的诚信（准确引用、不隐瞒反对意见）→ 对学术共同体的责任（推进理解、公正对待不同观点）→ 对社会的责任（研究问题的伦理考量、是否可能被误用）。

## 维度五：持续演进与深化

**核心问题：** 这个研究驱动了什么新的问题？

好的研究不终结对话，而是开启新对话。引导问题：如果被接受了，接下来什么问题浮现？什么希望回答但这次无法解决的问题？可能衍生出什么子项目？
```

- [ ] **Step 2: Write 维度六 (delivery and expression)**

From design doc 维度六 — keep concise, focus on key takeaways:

```markdown
## 维度六：交付与表达论证

当研究者卡在写作/表达阶段时使用。核心理念：写作本身是一种发现行为。

### 写作规划（§10）
三种常见障碍："还没准备好"型 / "完美初稿"型 / "结构瘫痪"型。

### 组织结构（§11）
读者视角：每段起点应是读者已知的，新信息放后半部分。

### 叙事弧线（§12）
有效叙事：起点（初始困惑）→ 冲突（知识缺口）→ 发展（论证递进）→ 解决/开放。

### 段落写作（§13）
每段第一句锚定任务，最后一句给出段落意义。

### 风格修改（§15）
被动语态过重、名词堆砌、主谓分离、抽象主语、模糊思考→清晰写作。

### 视觉（§16）
区分"视觉作为证据"（必须审视本身）vs "视觉作为修辞"（辅助理解）。

### 口头报告（§16）
核心不是涵盖所有——而是让听众带走一个核心概念。
```

- [ ] **Step 3: Commit**

```bash
git add skills/craft-of-research/SKILL.md
git commit -m "feat(craft-of-research): add dimensions 4-6"
```

---

### Task 6: Implement 引导策略总览（§3）

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append after dimensions)

**Interfaces:**
- Consumes: design spec §3 (all sub-sections: 3.1 question techniques, 3.2 fallback strategies, 3.3 So What cascade, 3.3.1 meaning levels, 3.4 innovation self-check engine)
- Produces: SKILL.md sections for §3

- [ ] **Step 1: Write question techniques table + fallback strategies**

```markdown
## 引导策略总览

### 提问技巧谱系
| 技巧 | 适用维度 | 示例 |
|------|---------|------|
| 聚焦追问 | 一 | "你说 X 很大。你具体关注哪个方面？" |
| 历史追问 | 一、二 | "这个概念从哪来？经历了什么变化？" |
| 结构追问 | 二 | "X 的组成部分有哪些？" |
| 反事实追问 | 二 | "如果 Y 变了，会发生什么？" |
| So What?级联 | 二、三 | "知道了这个，然后呢？" |
| 压力测试 | 三 | "如果你反对自己的论点，怎么说？" |
| Ethos检查 | 三、四 | "不同意你的人会觉得你公平吗？" |
| If-then测试 | 三 | "接受我的证据→是否必须接受主张？" |
| 叙事弧线追问 | 六 | "你的研究故事是什么？" |
| 风格伦理追问 | 六 | "读者会觉得你的思考和写作一样混乱吗？" |

### 兜底策略
| 卡住场景 | 策略 |
|---------|------|
| "我不知道我感兴趣什么" | "最近什么让你好奇或困惑？" |
| "我的问题太大了" | "如果只回答一小部分——你最想回答哪个？" |
| "我觉得没什么创新点" | 用创造性框架扫描文献中的位置 |
| "我想不到有什么意义" | 使用 So What? 级联 |
| "我的论证很弱" | "你最怀疑自己的哪个点？" |
```

- [ ] **Step 2: Write So What cascade + meaning levels**

```markdown
### 关键对话框架：So What? 深度级联

每次使用深入 3–5 层，逐层追问"所以呢？"直到自然停止。

**第一层**：Q1（具体问题）→ "所以呢？"
**第二层**：Q2（更重要的问题）→ "所以呢？"
**第三层**：重新思考 Y（根本信念/实践）→ "所以呢？"
**第四层**：影响实践/政策/理论 Z → "所以呢？"
**第五层**：自然停止

### 意义的层次标尺
1. 新信息（无需改变信念）
2. 解决困惑（调整某个理解）
3. 颠覆稳固信念（改变根本假设）
```

- [ ] **Step 3: Write innovation self-check engine**

From design doc §3.4:

```markdown
### 创新性自检引擎

五步诊断框架。研究者在哪步卡住就回到对应维度深化。

**Step 1 — 定位：** 我在和谁对话？（回到维度一）
**Step 2 — 意义：** 为什么有人应该在乎？（回到So What?级联）
**Step 3 — 论证拉力测试：** 我最薄弱的推理在哪？（回到维度三）
**Step 4 — 受众校准：** 谁会反对？为什么？（回到维度三 1c）
**Step 5 — 研究后果：** 然后呢？（回到维度五）

每步检查项来自设计 doc §3.4（约3-4个检查项/步）。
```

- [ ] **Step 4: Commit**

```bash
git add skills/craft-of-research/SKILL.md
git commit -m "feat(craft-of-research): add guidance strategies and innovation self-check"
```

---

### Task 7: Implement 输出格式 + 成功标准 + Final Polish

**Files:**
- Modify: `skills/craft-of-research/SKILL.md` (append at end, then verify)

**Interfaces:**
- Consumes: design spec §§4, 7
- Produces: SKILL.md complete file

- [ ] **Step 1: Write output format**

```markdown
## 输出

### 研究笔记（持续记录）
对话过程中记录关键产出。研究者可随时查看。

### 研究备忘录（可选）
当研究者觉得足够清晰时，生成结构化备忘录包含：研究问题、创造性切入点、论证骨架、潜在挑战、下一步问题。

### 保存
默认保存到 `research-notes/`。
```

- [ ] **Step 2: Write success criteria**

```markdown
## 成功标准

成功的标志不是"产出了一份计划"，而是研究者在对话中经历了以下转变：

- [ ] 从"我想研究 X"推进到"我想回答 Y 问题，因为它的答案会改变我们对 Z 的理解"
- [ ] 能说清研究在学术对话中的位置（同意什么/异议什么/扩展什么）
- [ ] 有清晰的"压力测试"意识——知道薄弱环节在哪里
- [ ] 知道"所以呢？"的答案——真正理解研究为什么重要
- [ ] 能提出新的问题——不仅是回答什么问题，而且是研究会催生的新问题
```

- [ ] **Step 3: Final read-through verify**

Read the complete SKILL.md. Check:
- [ ] YAML front matter correct (name, description, no trailing issues)
- [ ] Hard gate present
- [ ] Triggers match design doc §6
- [ ] All 6 dimensions present and distinct
- [ ] Creative framework includes both agreement and disagreement
- [ ] Self-check engine has all 5 steps
- [ ] Question techniques table populated
- [ ] Fallback strategies present
- [ ] So What cascade explained
- [ ] Output format defined
- [ ] Success criteria listed
- [ ] No placeholder text, TBD, or "implement later"
- [ ] Language consistent (Chinese primary, English terms preserved)

- [ ] **Step 4: Commit**

```bash
git add skills/craft-of-research/SKILL.md
git commit -m "feat(craft-of-research): add output format, success criteria, and final polish"
```
