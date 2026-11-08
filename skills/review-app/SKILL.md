---
name: review-app
description: Review a shipped or nearly shipped app in Daniel's workshop end to end, from purpose to verified fixes. Use when asked to review, QC, optimize or "get the most out of" an app such as Thumbwords, Globe & Atlas Orbits or relic-rack, before a wider release or App Store update, or when work feels busy but not better. Names the goal, corrects the written purpose, counts what is really in the build, does the goal math, QCs with a rubric-first pre-mortem, then hands fixes to one agent at a time and verifies with a different tool.
---

# Review App

## Overview

Agents polish whatever is in front of them. This skill points the work at what the app is *for*, measures from the code rather than the notes, and keeps the fix loop honest when Claude Code, Codex and Gemini share one tree.

Stay read-only until the user approves a change. Never change prices, store listings or submissions without explicit approval.

## Workflow

### 1. Name the goal: one question, then wait

Ask what the app is for. Typical answers and what they change:

| Goal | The review becomes |
|---|---|
| **Money** | installs × purchase rate × net price; getting found; paywall placement |
| **Showcase / credibility** | would an expert trust it (science, standards, honest labels) and share it (is the shareable thing free, does the copy sound confident) |
| **Craft / fun** | does a person enjoy it in motion; agents cannot feel motion, so the user's play notes are the spec |

If the user's request already answers this, skip the question. Otherwise ask only this, and wait.

### 2. Correct the written purpose

Read the project's `knowledge/context.md`. In every review so far it was stale (a "web experiment" that was a paid iOS app; "watch-only, no monetization" for an iPhone app with a purchase). Every agent works toward what that file says, so rewrite it to the confirmed goal, with provenance frontmatter, before anything else.

### 3. Count what is really in the build

Measure from code, not notes: import the modules or grep the data and count content, free vs paid, features, user-facing sentences. Notes drift; in Thumbwords they said the free dailies would run out, and the code showed they had already become a permanent collection. Report counts in a table with file references.

### 4. Do the goal math

- **Money:** price after Apple's cut (15% only once Small Business Program enrollment is confirmed, otherwise 30%) × assumed purchase rate × installs per day needed for the target. Label every input known, benchmark or guess. One-time unlocks do not accumulate; subscriptions need content that renews.
- **Showcase:** check the math and standards an expert would test first (formulas, export formats, units). Count defensive sentences (`not`/`no`) against total visible sentences; above roughly a quarter, the app sounds apologetic. Find whether the shareable output sits behind a paywall.
- **Craft:** turn the user's play notes into the spec; propose variants behind a toggle rather than one big pass.

### 5. QC the latest build

Use the prompt in `references/prompts.md` (QC section). Its parts are deliberate:

- Write the rubric **before** reading code, weighted by harm (lost money, lost saves, rejection, bad reviews).
- Pre-mortem: the three most likely one-star reviews and the code path behind each.
- Label evidence **[VERIFIED]**, **[INFERRED]** or **[NEEDS DEVICE]**.
- Check that the uploaded build matches the working tree (source edited after an archive is common).
- Check that test and layout scripts are current before trusting a failure or a pass.
- End with a ranked issue table, a 10-minute device checklist in play order, and the one question that most changes the ship call.

### 6. Fix with one agent at a time, verify with another

- Split by access: the agent with the build/release pipeline and App Store Connect access (usually Codex) builds and uploads; text, research and review can run elsewhere because they write separate files.
- Only one agent edits the project tree at a time. When others are active, append to shared knowledge files, never rewrite them.
- Before any archive: commit and tag the tree, bump the build number, and leave a SESSION.md handoff naming the tag.
- When an agent reports "done", confirm a new commit exists before reviewing. A claimed finish with no commit happened once.
- Review with a different tool than the builder: check each approved change exactly (grep old and new strings), and look at the screenshots yourself.

Record each decision the user makes in `knowledge/DECISIONS.md` and keep a running status table in chat.

## Outputs

- A goal statement in `knowledge/context.md`.
- Count and math tables (inline or `docs/`).
- A QC report: rubric, pre-mortem, graded checks with evidence labels, ranked issues, device checklist, deciding question.
- Copy-ready prompts for the building agent (`references/prompts.md`).
- A pass/fail review of the agent's commit.

## References

- `references/prompts.md`: the framing prompt, the QC prompt, and handoff prompt templates.
- `references/case-notes.md`: what each past review found, for calibration.
