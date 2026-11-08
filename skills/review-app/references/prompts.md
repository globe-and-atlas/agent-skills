# Review App prompts

Copy-ready. Replace `{…}`.

## Framing (step 1)

```text
I'm trying to {goal in my words}. Here is my current question: {question}.
Here is the relevant context: {context}.
Identify three plausible underlying problems I might actually need to solve.
Explain how each would change the advice. Identify the assumption in my
framing most likely to mislead us. Ask the single question whose answer
would most change your recommendation, then wait.
After I answer, formulate a better question and address it. Distinguish
what you inferred from what I explicitly told you.
```

## QC (step 5)

```text
You are QC for {app} {version} (build {build}) before it goes to {TestFlight / review}.
Your job is to find reasons NOT to ship, not to confirm that it works.
Do not fix anything until I approve the report.

Context: Read knowledge/context.md, knowledge/DECISIONS.md (last 10 entries),
and the store listing. The app exists to {goal}. {privacy promise}.
The last public build is {public build}; review what changed since then.

Step 1. Rubric first. Before you look at the code, write the 8 checks a
strict App Store reviewer and a {paying customer / expert user} would use to
judge this build. Weight them by harm if they fail: lost money, lost saves,
rejection, bad reviews. Cover at least: {purchase and restore, saved progress
across the update, every feature starting and finishing, iPhone and iPad
layouts, Day/Night, content safety, no hidden data collection}.

Step 2. Pre-mortem. Assume that one week after release, this build got a wave
of one-star reviews. Write the three most likely reviews and the code path
behind each.

Step 3. Check. Grade the build against the rubric. Run the test suite and the
build. Confirm the uploaded build matches the working tree. For each check,
label your evidence:
  [VERIFIED] you ran or read something that proves it (say what)
  [INFERRED] the code suggests it, but you did not exercise it
  [NEEDS DEVICE] only a person on a real device can confirm it
Try to break each check: name the specific input or step that would make it fail.

Step 4. Report. A table ranked by release risk with columns: issue, evidence
label, what a user would experience, the smallest fix, and "blocks release?"
yes/no. Then a checklist of everything labeled NEEDS DEVICE, in the order I'd
hit it in a 10-minute session, each with the one thing to watch for.

End with: the one question whose answer would most change your ship/no-ship call.
```

## Handoff to the building agent (step 6)

```text
In {project}, read knowledge/context.md, the latest knowledge/DECISIONS.md
entry, and {spec doc}. Implement exactly:
{numbered changes, each testable}
{Constraints: what must not change; labels that must never be used.}
Build {targets}, run the test suites, capture before/after screenshots of
{screens}. Commit together with {uncommitted docs to include}. Leave
{files to leave untouched} uncommitted. Tag the commit, leave a SESSION.md
handoff, and end your reply with the commit hash and tag.
Do not {submit / change prices / publish}.
```

## Review of the agent's commit (step 6)

1. `git log` and `git tag`: a new commit and tag exist.
2. For every approved text change: grep that the old string is gone from visible text (allowed in accessibility labels if the spec says so) and the new string is present.
3. Grep for forbidden words in visible strings.
4. Read the build and test lines in the handoff; open the screenshots.
5. Report pass/fail per requirement with evidence, plus small notes that don't block.
