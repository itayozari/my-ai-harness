# agent-hq — Quick Start

Your day-to-day reference for using this HQ. Updated whenever a new specialized agent (skill) is added.

## Open the HQ

```
cd <path-to-this-repo>
claude
```

## Slash Commands

| Command | What it does |
|---------|-------------|
| `/onboard` | First-time setup. Captures the project, your communication style, and any existing knowledge you want to seed. |

<!-- New skills get a row here automatically when they're built. -->

## Common Prompts (no command needed)

| What you want | Just say |
|--------------|---------|
| Start working on something new | "let's work on \<thing\>" |
| Make the work into a reusable agent | "this is going to be a skill — \<thing\>" before starting |
| Update the HQ's knowledge | "should we update context?" (usually at session end) |
| Review what's recorded about the project | "show me what's in CLAUDE.md / STATE.md / docs/" |
| Find a past output | "what's in workspace/?" or "find the \<topic\> output" |

## Key Files

| File | What it is |
|------|-----------|
| `CLAUDE.md` | The HQ's spine. Project, communication style, skill index. |
| `STATE.md` | Where the project stands right now. Read every session. |
| `docs/META.md` | The manifesto: four-layer model, principles. |
| `docs/CONTEXT-PROTOCOL.md` | How knowledge gets updated. Loaded on demand. |
| `docs/BUILDING.md` | How new skills and tools get built from real work. |
| `skills/` | Your specialized agents. Each one handles a slice of the work. |
| `tools/INDEX.md` | Runtime registry of code/integrations skills can use. |
| `workspace/` | All work product. Organized by domain. |

## Adding a New Specialized Agent (Skill)

You don't pre-build them. You do the work first, flagged as future skill, and the system captures it. See `docs/BUILDING.md` for the flow.

In short:
1. Tell the agent: *"this is going to be a skill — \<task\>"*
2. The agent does the work deliberately — building tools, structuring the workspace, noting decisions
3. At the end, the work is captured into `skills/<name>/`, registered in `CLAUDE.md` → Skill Index, and a `/<name>` slash command is added here
