---
name: simple-explainer
description: Use when the user asks to explain something "simply", "really simply", "again simply", "in plain words", or says they don't get an explanation, intuition, or slide — especially for math, CS, or course concepts (numerical methods, error, stability, interpolation, ODEs).
---

# Simple Explainer

## Overview
Explain at the "ball in a bowl" level: one everyday picture carries the idea, a tiny worked number proves it, and one line sums it up. The reader should get it in under 30 seconds.

## The reply IS these parts, in this order
1. **One-sentence answer.** The idea in everyday words, no symbols.
2. **The picture.** One everyday scene (ball in a bowl, car speedometer, walking in fog). Two or three short bullets that map it to the idea: small case → good, big case → bad.
3. **Numbers.** The smallest worked example that shows it happening: 3–5 steps of arithmetic with round numbers (1, 2, 10, 0.5). Use arrows (`1 → 0.5 → 0.25`) or a 3-row table.
4. **The check.** The one formula or test the student needs, written as a plain rule (`|g| < 1 → stable`). At most two bullets.
5. **Why we care.** One or two sentences linking back to the course question.

Total: about 120–200 words. Bold the key words. Short lines.

## Choosing the picture
- Physical and familiar: motion, money, cooking, walking, driving.
- It must show the failure case too (overshoot, drift, blow-up), not only the good case.
- Use the same picture throughout the reply. One picture, not three.

## Choosing the numbers
- Pick values that make arithmetic trivial (λ = 10, h = 0.05 vs 0.3; y′ = 2y, y₀ = 3).
- Show the good case and the bad case side by side when the idea is a contrast.
- If a claim is "the h² terms cancel" or "error shrinks 8×", show the numbers that prove it instead of asserting it.
- For an "error is O(hᵖ)" claim, compute the error at h and h/2 and show the ratio (4× → h², 8× → h³).

## Quick reference
| Part | Length | Form |
|---|---|---|
| Answer | 1 sentence | plain words |
| Picture | 2–3 bullets | everyday scene |
| Numbers | 3–5 steps | arrows or tiny table |
| Check | 1–2 bullets | rule with symbols |
| Why | 1–2 sentences | link to course |

## Common mistakes
| Mistake | Fix |
|---|---|
| Opening with the formula or Taylor series | Open with the one-sentence answer and the picture; formula goes in "The check" |
| Asserting a result ("terms cancel", "it's symmetric") | Show it with tiny numbers |
| Extra sections (rule of thumb, global vs local aside, history) | Keep to the five parts; offer the extra in one line at the end |
| Several analogies | Pick one and stick with it |
| Undefined jargon ("order p", "amplification factor") | Say it in words first, then name it in parentheses |

If the student asks for a derivation, a proof, or "step by step", give the full working instead and keep the picture as a one-line opener.
