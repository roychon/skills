---
name: writing-notion-notes
description: Write or edit notes in Notion so they render cleanly and read well — finding where a page belongs, structuring it, Notion markdown that actually works (toggles, callouts, tables, code), safe edits to existing pages, and verifying the result. Use whenever creating a Notion page of notes (lecture/study notes, meeting or research notes, summaries, how-tos) or adding to, restructuring, or cleaning up an existing notes page.
---

# Writing Notion Notes

Notes in Notion must read cleanly: no raw tags, no run-on blocks, every question collapsible. The Notion MCP's markdown differs from the published spec in ways that silently break pages, so follow section 4 exactly and always verify (section 6).

## 1. Find the destination (read-only first)

- Search Notion using everything you know: the topic, source title/file name, working folder name, anything the user said. Fetch the best candidates and look at how they're organized (a parent page, a notes section, sibling pages and their titles).
- Pick one parent and a title that follows the siblings' naming pattern (e.g. "Lecture 2" → "Lecture 3"); with no pattern, use the source's own title or a short descriptive name.
- **Ask once, naming the exact path:** "Want me to add this as <title> under <parent path>?" If no clear match, give your best guess or two. Write nothing without a clear yes; if the user names a different place, use theirs.
- If a page with that title already exists there, ask whether to add to it or replace it. Never overwrite silently.
- After creating, if the parent lists its child pages somewhere (e.g. a "Lectures" or "Notes" heading), add the new page's link there in order — fetch the parent first and keep the rest intact.
- When the user asks to add to a page they've already named or that this conversation created, skip the search and ask — just edit it (section 5).

## 2. Page structure

```txt
<callout 📄 gray_bg>  what this is · source/scope · date or link if relevant
<table-of-contents />
---
## 1. Section title            ← add "(slides x–y)" / "(pp. x–y)" when the source has numbers
   short paragraphs, bullets, tables, code
   <callout 🧠 gray_bg> Metaphor / intuition (optional; standard for study notes)
   ### Questions               ← only if the user asked any
      one <toggle> per question: user's own wording as the title, answer inside
---
## 2. ...
---
## Recap / Summary             ← 2–4 sentences tying it together
```

Callout conventions:
- 🔑 `yellow_bg` — anything the user flagged as important or a key mental model.
- 🗺️ `blue_bg` — diagrams, flows, "who talks to whom".
- 🧠 `gray_bg` — metaphor / intuition.
- ⚠️ `orange_bg` — gotchas, common mistakes, corrections.

Adapt the template to the content (meeting notes: Decisions / Action items / Discussion; research: Question / Findings / Sources). Keep the header callout, TOC, dividers, and toggled Q&A whenever they fit.

## 3. Writing style

- Short paragraphs (1–3 sentences). Prefer bullets over long prose; one idea per bullet.
- Numbered lists only for real sequences (steps, ordered stages).
- Bold the key term in each bullet, not whole sentences.
- Tables for comparisons of 2+ things across 2+ attributes.
- Code and command examples in code blocks with a language tag (`python`, `txt`, `bash`, `sql`).
- Cite sources inline where a point comes from one place ("slide 41", "p. 12", a link).
- Mark anything not in the source as *Not on slides* / *Not in source*. Call out source errors or outdated claims explicitly instead of copying them.
- Fold in what made things click: if a rephrase or simpler take landed with the user, use that version, not the first draft.

## 4. Notion markdown that works (via the Notion MCP)

Every rule here was learned from a page that broke.

**Toggles** — use `<toggle>`; first line is the title; children are separate blocks split by blank lines, **not indented**:

````txt
<toggle>
Question title in the user's words

Answer paragraph with **bold** and `code`.

- bullet
- bullet

```python
x = 1
```
</toggle>
````

- ❌ `<details><summary>…</summary>…</details>` — lands as raw escaped text.
- ❌ Tab-indented children — squashed into one paragraph; code blocks become inline code.
- ❌ `### Heading {toggle="true"}` — the attribute shows as raw text.
- ❌ Tables inside a toggle — validation fails ("bare `<tr>`"). Convert to bullets (`**Item** → explanation`). Tables are fine at the top level.

**Callouts** — same style: `<callout icon="🔑" color="yellow_bg">`, then unindented blocks split by blank lines, then `</callout>`. Code blocks and lists inside work.

**Formatting** — Markdown only: `**bold**`, `*italic*`, `` `code` ``. Never HTML (`<b>`, `<i>`, `<br>`, `<code>`); the fetched view shows those, but don't copy them back.

**Other**
- Pipe tables (`| a | b |`) at the top level render fine.
- Nested bullets: a tab-indented `- item` under a top-level bullet works.
- Divider: `---` on its own line. Table of contents: `<table-of-contents />`.
- Outside code, escape or avoid literal `< > { } [ ] | ~` in prose (wrap them in backticks, or reword — e.g. "≈" instead of "~").
- Inside code blocks, write content literally; no escaping.

## 5. Editing an existing page

- **Fetch first.** Large fetches are saved to a file; parse with Python (`json.loads` → `text`) and search for the spot instead of reading it raw.
- **Smallest edit:** use `update_content` with an `old_str` of plain text near the target. The fetched view renders formatting as `<b>`/`<i>`/`<code>`, so anchor on a run of text without formatting (e.g. the last sentence of a toggle plus `\n</toggle>`).
- **Placement:** a new Q&A goes as a toggle at the end of the matching section's Questions (create the `### Questions` heading if missing); new reference material goes beside related content in that section.
- Use `insert_content` only to prepend/append to the page. Use `replace_content` only for a full rewrite the user asked for; preserve any child `<page>`/`<database>` tags and never pass `allow_deleting_content` without confirmation.
- **Testing a format:** if unsure a construct will render, append a small `TEST` block, fetch, check, and make sure it's removed afterwards.
- If the notes have a local log (e.g. `.notes/<name>.md`), append the same addition there too.

## 6. Verify every write

Fetch the page again and check, with a short Python script over the saved fetch:
- `\<` count is **0** (no escaped raw tags) and `<br` count is **0**.
- Toggle count is what you expect (previous + added).
- New content sits in the intended section (its index falls before the next `## ` heading).
- No leftover `TEST` blocks.

Fix anything off, then finish by giving the user the page link and one line on what changed and where.
