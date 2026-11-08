# Agent skills

Reusable skills from the Globe & Atlas workshop, written for coding agents such as Claude Code and OpenAI Codex.

| Skill | What it does |
|---|---|
| [`review-app`](skills/review-app/SKILL.md) | Review a shipped or nearly shipped app from its goal to verified fixes: name what it's for, correct the written purpose, count what's really in the build, do the goal math, QC for reasons not to ship, then fix with one agent at a time and verify with a different tool. |

## Install

Copy a skill folder into your agent's skills directory, for example:

- Claude Code: `.claude/skills/review-app/` in a project, or `~/.claude/skills/review-app/`
- Codex: `.agents/skills/review-app/`

Each skill is a `SKILL.md` with YAML frontmatter plus optional `references/` and `agents/` files.

## Background

These skills come out of working sessions at [Globe & Atlas](https://globeandatlas.substack.com). They assume a project keeps its purpose in `knowledge/context.md` and its decisions in `knowledge/DECISIONS.md`; adapt the paths to your own conventions.
