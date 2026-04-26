# agent-hq

A template repo for setting up an HQ of agents around any project, using Claude Code.

Not a framework. Not an automation platform. A structured workspace where four layers compound over time around one project:

- **Skills** — specialized agents you build for parts of the work (each skill = one agent)
- **Knowledge** — context you and the agents share about the project, you, the domain
- **Tools** — code, scripts, integrations the agents can run
- **Outputs** — work product the agents have produced

Anyone with a project can use it. Building a SaaS, writing a thesis, running a law practice, managing a brand, studying for an exam — any project. The repo defines no project — you do, on first run.

## How to start

1. Fork or clone this repo.
2. `cd` into it and open Claude Code.
3. Either run `/onboard` and let Claude walk you through setup, **or** just start working — Claude will ask the bare minimum it needs (your project + how you want to work) before doing anything.

That's the whole setup.

## How it grows

You don't pre-build skills, tools, or knowledge. You do real work. When a task is going to repeat or matters enough to standardize, flag it: *"this is going to be a skill"*. Claude runs the work deliberately — building tools, structuring workspace output, noting decisions — and at the end captures all of it into a reusable skill (= a specialized agent you can rerun later).

The HQ fills up from your work, not from speculation about what you might need.

## The principles

Read `docs/META.md` for the full manifesto. Short version:

1. Build only when real work demands it. No speculative skills, tools, or docs.
2. Knowledge is the product. Every session deepens context.
3. Skills define *what*, tools define *how*. Skills discover tools at runtime, so capabilities and execution evolve independently.
4. Pointers over content. Context files reference where things live, never duplicate them.
5. The HQ builds itself. Recurring work becomes skills. Deepening domains become knowledge.

## Repo layout

```
agent-hq/
├── CLAUDE.md            # The spine — agent instructions, project, skill index
├── STATE.md             # Where the project is right now (~80 lines max)
├── docs/                # Manifesto, protocols, building guides, examples
├── skills/              # Your specialized agents (start empty; grow over time)
├── tools/               # Your tools, registered in tools/INDEX.md
└── workspace/           # All work product, organized by domain
```

## Updates from upstream

This is a fork-once template. We don't push updates that overwrite your customized `CLAUDE.md` / `STATE.md`. If we improve `docs/META.md`, the building guides, or the templates, you can pull those manually — but anything you've personalized is yours.

## License

MIT — fork it, modify it, use it however you want.
