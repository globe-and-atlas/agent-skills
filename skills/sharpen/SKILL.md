---
name: sharpen
description: Upgrade the user's question into a better one before answering. Use when the user types /sharpen, asks to sharpen, reframe or upgrade a question or request, or asks "what should I really be asking?". Finds the goal the question serves, gathers project context without asking, names the hidden assumption, offers sharper, deeper and bolder rewrites (the bolder one uses a capability the user may not know about, with the agent and output that fit), then answers the best version or asks the single deciding question.
---

# Sharpen

## Overview

The usual limit isn't the model; it's knowing what to ask. This skill turns a rough question into the one that makes best use of the tools, then answers it. In practice, "how do I optimize my app before launch?" becomes "can this app reach my revenue target with the hours I have, and when should I stop?", and "give me clever prompts" becomes "what is falling short in my actual work?". Without the skill, getting there took several turns; with it, it takes one.

## Workflow

Work through these steps, then show the result in the output format below.

1. **Goal.** In one line: what decision or outcome does the question serve, and what will the user do differently once they have the answer?
2. **Context.** Gather what's relevant without asking: the project's own notes (for example `knowledge/context.md`, a session log, a decisions log, the README), any record of which agents and tools have worked well for this user, and the code itself when the question is about a project. Label each fact **[READ]**, **[TOLD]** or **[ASSUMED]**.
3. **Hidden assumption.** Name the assumption in the wording most likely to send the answer the wrong way.
4. **Upgrade.** Rewrite the question three ways:
   - **Sharper:** same scope, specific and measurable, with what "done" looks like.
   - **Deeper:** the underlying problem the question points at.
   - **Bolder:** the version the user wouldn't think to ask, using a capability they may not know about: counting from the code, running and comparing variants, simulating, generating a file (STL, GeoJSON, audio, images), a 15-minute probe build, or checking against a published standard.
   For each, name the agent or tool that fits and the concrete output.
5. **Decide.**
   - If the original question was already good, say so and answer it.
   - If one missing fact would change everything, ask that single question and wait.
   - Otherwise recommend one upgraded version and answer it.

## Output format

```text
Goal: …
Hidden assumption: …
Sharper: … (agent → output)
Deeper: … (agent → output)
Bolder: … (agent → output)
Going with: <which, and why in one line>
<the answer, or the one question>
```

Keep the upgrade block short. The value is in the answer that follows.

## Guardrails

- Don't interrogate. One question at most, and only if it changes the answer.
- Don't inflate a simple request. "Just answer it" is a valid outcome.
- Stay read-only while gathering context.
- For visual, motion or sound work, say that the user's own look-and-feel verdict is the real test. Agents reliably produce code that runs and passes tests but misses the intended look or feel.
