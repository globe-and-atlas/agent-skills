# Agent skills

Reusable skills from the Globe & Atlas workshop, written for coding agents such as Claude Code and OpenAI Codex.

| Skill | What it does |
|---|---|
| [`review-app`](skills/review-app/SKILL.md) | Review a shipped or nearly shipped app from its goal to verified fixes: name what it's for, correct the written purpose, count what's really in the build, do the goal math, QC for reasons not to ship, then fix with one agent at a time and verify with a different tool. |
| [`sharpen`](skills/sharpen/SKILL.md) | Upgrade a rough question before answering: find the goal it serves, gather project context, name the hidden assumption, offer sharper, deeper and bolder rewrites (the bolder one uses a capability you may not know about), then answer the best one. Use `/sharpen` in Claude Code or `$sharpen` in Codex. |

## Install

Copy a skill folder into your agent's skills directory, for example:

- Claude Code: `.claude/skills/<skill>/` in a project, or `~/.claude/skills/<skill>/`
- Codex: `.agents/skills/<skill>/`

Each skill is a `SKILL.md` with YAML frontmatter plus optional `references/` and `agents/` files.

## Background

These skills come out of working sessions at [Globe & Atlas](https://globeandatlas.substack.com). They assume a project keeps its purpose in `knowledge/context.md` and its decisions in `knowledge/DECISIONS.md`; adapt the paths to your own conventions.
