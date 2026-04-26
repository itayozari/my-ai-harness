<!--
Agent template. An agent is an orchestration — a task definition that combines
multiple skills with its own triggers and specialization.

Agents are an OPTIONAL layer in the harness. Many users will never need one.
Use an agent when:
  - The task naturally spans multiple skills that need to be coordinated.
  - There's specialized competency or quality bar that lives above any
    single skill.
  - The orchestration itself is the reusable thing.

If an "agent" doesn't add anything beyond chaining its skills, you don't need
an agent — just put a slash command pointing to the skill (or skills) directly.

Copy this folder to `agents/<your-agent-name>/`, fill it in, optionally create a
slash command at `.claude/commands/<your-agent-name>.md`, and register the agent
in `CLAUDE.md` → Agent Index.

Delete every <placeholder> and every <!-- comment block --> before saving.
-->
# <Agent Name>

## Purpose
<One paragraph. What this agent does — the kind of task it executes, what "done"
looks like.>

## Skills it pulls from
<Each skill applies its own process inside this agent.>

| Skill | How this agent uses it |
|-------|------------------------|
| `skills/<skill-name>/` | <how it's used here> |
| `skills/<skill-name>/` | <how it's used here> |

## Triggers
<When this agent activates.>

- `/<command>` — <if a slash command exists>
- "<phrase>" — <user-spoken trigger, e.g., "let's plan a launch">

## Specialized competency
<What this agent does that goes beyond just chaining its skills. Domain
knowledge, quality bars, decisions, behaviors specific to this orchestration.
If there's nothing real here, you may not need an agent.>

## Orchestration
<How the skills get sequenced or combined. Conditions, dependencies, parallel
vs. sequential.>

1. <step>
2. <step>
3. <step>

## Tool check
Before executing, scan `tools/INDEX.md` for capabilities relevant to this agent.

## Storage
<Where outputs from this agent go in `workspace/`. May follow the convention of
one of the underlying skills, or define a new one.>

## Notes
<Optional. When this agent should defer to a single skill instead. Edge cases.>
