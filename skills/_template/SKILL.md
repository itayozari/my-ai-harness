<!--
Skill template. A skill is a reusable process for a kind of work that repeats.

Copy this folder to `skills/<your-skill-name>/`, fill it in based on the work
that just happened (or that is about to happen when the user has flagged a task
as a future skill), and register it in `CLAUDE.md` → Skill Index.

Delete every <placeholder> and every <!-- comment block --> before saving.
-->
# <Skill Name>

## Purpose
<One paragraph. What this skill does. What "done" looks like. Be concrete enough
that the AI reading this knows whether to load this skill for a given task.>

## When to Use
<The trigger. Be specific so the agent picks the right skill in future sessions
when multiple skills exist. Example: "Writing social posts for any platform" vs
"Writing performance ad copy where conversion matters more than stopping power" —
two different triggers, two different skills.>

## Core Principles

<3-7 numbered principles that shape every run of this skill. This is where the
quality bar lives. These came out of how the work was actually done — they're
not invented in the abstract.>

1. **<Principle name>.** <One-line statement of the rule, plus a sentence on why.>

2. **<Principle name>.** <One-liner.>

3. **<Principle name>.** <One-liner.>

## Process

<If the process is short (<5 steps), inline it here. If it's longer, point to
PROCESS.md in the same folder.>

Before executing, scan `tools/INDEX.md` for capabilities relevant to this skill.
A new tool added to the registry today is available to this skill from now on,
with no edits to this file.

<Inline steps OR: "Follow the process defined in `PROCESS.md`. Never skip the
<critical-step> step.">

## Reference Files

<Table of any sibling files this skill uses. Loaded on demand, not all at once.>

| File | Purpose |
|------|---------|
| `PROCESS.md` | <one-liner — only if the process is long enough to warrant its own file> |
| `<RUBRIC.md>` | <one-liner — e.g., quality scoring rubric, source-evaluation criteria> |
| `<EXAMPLES.md>` | <one-liner — annotated examples of strong/weak outputs> |

## Storage

All outputs from this skill go to `workspace/<domain-folder>/<naming-convention>`.

<Specify the exact folder structure and file naming. Example:
"workspace/research/<topic-slug>/findings.md" or
"workspace/contracts/<client>/<contract-name>/redline.md".

This is the convention every future run inherits — get it right on the first
deliberate run.>

<If the skill maintains an index across runs:
"After completing any run, append a row to `workspace/<domain>/INDEX.md`.">

## Notes

<Optional. Anything else the agent needs to know. Common pitfalls, edge cases,
when this skill should defer to a different skill.>
