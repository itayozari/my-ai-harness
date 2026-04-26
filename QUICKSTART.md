# my-ai-harness — Quick Start

Your day-to-day reference for using this harness. Updated whenever a new skill or agent is added.

## Open the harness

```
cd <path-to-this-repo>
claude
```

(Currently wired for Claude Code. Adapt the open command if you're using a different tool.)

## Slash Commands

| Command | What it does |
|---------|-------------|
| `/onboard` | First-time setup. Captures the project, communication style, and any existing knowledge you want to seed. |

<!-- New skills and agents get a row here when they're built. -->

## Common Prompts (no command needed)

| What you want | Just say |
|--------------|---------|
| Start working on something new | "let's work on \<thing\>" |
| Make the work into a reusable skill | "this is going to be a skill — \<thing\>" before starting |
| Update the harness's knowledge | "should we update context?" (usually at session end) |
| Review what's recorded about the project | "show me what's in CLAUDE.md / STATE.md / docs/" |
| Find a past output | "what's in workspace/?" or "find the \<topic\> output" |

## Key Files

| File | What it is |
|------|-----------|
| `CLAUDE.md` | The harness's spine. Project, communication style, skill index, agent index. |
| `STATE.md` | Where the project stands right now. Read every session. |
| `docs/META.md` | The manifesto: parts of the harness, principles. |
| `docs/CONTEXT-PROTOCOL.md` | How knowledge gets updated. Loaded on demand. |
| `docs/BUILDING.md` | How new skills, agents, and tools get built from real work. |
| `skills/` | Your reusable processes. |
| `agents/` | *(optional)* Your orchestrations that combine multiple skills. |
| `tools/INDEX.md` | Runtime registry of code/integrations skills and agents can use. |
| `workspace/` | All work product. Organized by domain. |

## Adding a New Skill

You don't pre-build them. You do the work first, flagged as future skill, and the harness captures it. See `docs/BUILDING.md` for the flow.

In short:
1. Tell the AI: *"this is going to be a skill — \<task\>"*
2. The AI does the work deliberately — building tools, structuring the workspace, noting decisions.
3. At the end, the work is captured into `skills/<name>/`, registered in `CLAUDE.md` → Skill Index, and a `/<name>` slash command is added here.

## Adding a New Agent (Optional)

Build an agent only when work needs to coordinate multiple skills as a single orchestrated task. If a skill alone covers it, build the skill. See `docs/BUILDING.md` → "Building an agent".
