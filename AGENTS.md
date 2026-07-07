# craft-of-research

A project containing the full text of *The Craft of Research* (5th Edition) as a Markdown document, a Socratic research-guide agent skill derived from the book, and planning/spec documents for the skill's implementation.

## STRUCTURE

```
.
├── book/                          # 📚 Book content + figures
│   ├── craft-of-research-5e.md    # Full book text (~4800 lines)
│   └── figures/                   # 29 images (cover, figures, logo)
├── skills/
│   └── craft-of-research/
│       ├── SKILL.md               # Thin shell: language selection (~34 lines)
│       ├── SKILL-zh.md            # Full Chinese version (~716 lines)
│       └── SKILL-en.md            # Full English version (~720 lines)
├── examples/                      # Sample skill dialogues (EN/ZH × humanities/science)
│   ├── humanities-en.md           # Humanities dialogue — English
│   ├── humanities-zh.md           # Humanities dialogue — 中文
│   ├── science-en.md              # Science dialogue — English
│   └── science-zh.md              # Science dialogue — 中文
├── docs/superpowers/
│   ├── plans/                     # Implementation plans
│   └── specs/                     # Design specifications
└── .omo/run-continuation/         # Agent session state (auto-generated)
```

## WHERE TO LOOK

| Need | Path |
|------|------|
| Book content (full text) | `book/craft-of-research-5e.md` |
| Book figures | `book/figures/fig-{chapter}-{number}.jpg` |
| Agent skill (research guidance) | `skills/craft-of-research/SKILL.md` |
| Skill — Chinese version | `skills/craft-of-research/SKILL-zh.md` |
| Skill — English version | `skills/craft-of-research/SKILL-en.md` |
| Example dialogue — humanities (EN) | `examples/humanities-en.md` |
| Example dialogue — humanities (ZH) | `examples/humanities-zh.md` |
| Example dialogue — science (EN) | `examples/science-en.md` |
| Example dialogue — science (ZH) | `examples/science-zh.md` |
| Skill implementation plan | `docs/superpowers/plans/` |
| Skill design spec | `docs/superpowers/specs/` |

## CONVENTIONS

- **Image naming**: `fig-{chapter}-{number}[a].jpg` — e.g., `fig-05-04a.jpg` for Chapter 5, Figure 4a
- **Special images**: `cover.jpg`, `chicago-logo.jpg`, `infinity-symbol.jpg` at root of `book/figures/`
- **Skill format**: YAML frontmatter + Markdown body, `name: craft-of-research` in frontmatter
- **Bilingual skill**: Chinese primary with English key terms; language selection via `question` tool
- **File paths**: All image references in the book use relative paths (`figures/...`)

## ANTI-PATTERNS

- **Do NOT edit `docs/superpowers/`** — content is read-only reference
- **Do NOT rename image files** without updating all `![](...)` references in `craft-of-research-5e.md`
- **Do NOT edit `.omo/run-continuation/`** — auto-generated session state
- **Do NOT add code files** — this is a content + skill project, no build system

## COMMANDS

| Command | Action |
|---------|--------|
| `/craft-of-research` | Invokes the research guidance skill |

## NOTES

- 4802-line Markdown file with 29 embedded figures
- LSP not relevant — no code to analyze
- `skills/craft-of-research/SKILL.md` self-documents; no AGENTS.md needed there
- The skill distills the book's methodology into a Socratic dialogue framework
