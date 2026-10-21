# skills

My personal [Claude Code](https://claude.com/claude-code) skills.

| Skill | What it does |
| --- | --- |
| [`concept-explainer`](concept-explainer/SKILL.md) | Explains material (slides, docs, pasted text, or a topic) one section at a time, gated on your go-ahead: outline with slide ranges, simple explanation + metaphor per section, a running notes log, and an offer to save to Notion at the end. |
| [`writing-notion-notes`](writing-notion-notes/SKILL.md) | Writes notes to Notion that render cleanly: finding the right page, a consistent page template, Notion markdown that actually works (toggles, callouts, tables, code), safe edits, and verifying every write. |

## Install

Copy a skill folder into `~/.claude/skills/` (personal, all projects) or `.claude/skills/` (one project):

```bash
git clone https://github.com/roychon/skills.git
cp -R skills/concept-explainer skills/writing-notion-notes ~/.claude/skills/
```

`concept-explainer` hands its Notion step to `writing-notion-notes`, so install both if you use Notion.
