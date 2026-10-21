---
name: concept-explainer
description: Explain a concept, topic, or body of material (course slides, a document, pasted text, or a raw topic name) one section at a time, gated on the user's explicit go-ahead. Use when the user asks you to explain, walk them through, teach, or break down a concept, topic, or set of slides/material step by step, especially when they want it kept simple and want to learn at their own pace.
---

# Concept Explainer

Explain in **gated** sections: one section per turn, each stopped by an explicit go-ahead from the user before the next one is written.

## 1. Gather the material

If the user hasn't given you the material yet (slides, a document, pasted text, or just a topic name), ask for it, or, for a bare topic, confirm scope before proceeding.

## 2. Group into sections

Read the whole material first. Group related content into a small number of logically coherent sections — each section should be one tight idea or cluster of closely related ideas, not one slide per section and not the whole topic as one section. Aim for sections a person could each absorb in under a minute.

**Done when:** you have an ordered list of section titles that, in sequence, cover the whole material with no gaps or overlap.

When the material has slide or page numbers, record which slides each section covers, using the number printed on the slide (not the PDF page index, which can drift when slides are skipped or a note spills onto an extra page).

Show the user this outline (titles only, plus each section's slide range when the material has one, e.g. "3. Map and Reduce (slides 13–19)") before starting, so they know how many stops there are. Do not summarize or explain any section's content here — titles only.

## 3. Explain one section

For the current section, write:
- The section heading with its slide range when the material has slide numbers (e.g. "## 3. Map and Reduce (slides 13–19)"), and cite specific slide numbers inline where a point comes from one slide (e.g. "the mean example on slide 41").
- A **very simple, concise explanation** — plain language, no jargon left undefined, short enough to read in one breath.
- One **metaphor or analogy** that makes the idea visualizable and sticky.

Then stop. End the turn by explicitly asking whether they're good to move on (e.g. "Good to move on, or want to go deeper here?").

Write exactly one section's explanation per turn, regardless of how many sections remain.

## 4. Gate on explicit approval

Only advance to the next section on an unambiguous go-ahead (e.g. "ok", "got it", "next", "yes", "continue", "moving on"). A question, a request to rephrase, a tangent, or no clear signal is not approval — stay on the current section, answer what they asked, and re-ask before moving on.

**Done when:** the user's message is an explicit, unambiguous signal to proceed.

**Keep a running log.** Once the outline is shown, create a notes file in the material's folder (or the working directory for a bare topic) at `.notes/<material name>.md`, starting with the outline. In the same turn as each section's explanation, append it. In the same turn as you answer any question, rephrase, or extra example, append the user's question in their own words and your answer under the current section. Never defer logging to the end: long sessions get compressed and can end early, and the log is what step 6 builds from.

## 5. Repeat, then close

Repeat steps 3–4 for each remaining section in order. After the last section is approved, give a short recap tying the sections together — a sentence or two, not a re-explanation.

## 6. Offer to save to Notion

Use the `writing-notion-notes` skill for everything Notion: finding the destination, asking once before writing, page structure, the markdown that renders, and verification.

What goes on the page, built from the running log (`.notes/<material name>.md`) plus the conversation, not just your first drafts — one `##` section per outline section, in order, with its slide range in the heading:
- **Explanation:** the full explanation, rewritten to fold in whatever made it click for the user.
- **Metaphor:** the analogy, or the better one if you switched mid-way.
- **Questions:** each question the user asked about that section and its answer, as toggles (the user's own wording as the title). Omit if none.
- Anything the user flagged as important as a 🔑 callout in its section.

Leave out off-topic tangents. End the page with the recap, and give the user the page link.
