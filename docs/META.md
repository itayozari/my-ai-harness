# What Is agent-hq

A method for setting up an HQ of agents around any project. Not a framework, not an automation platform — a structured workspace where four layers compound over time around one project.

The HQ is owned by you. Inside it lives a growing team of specialized agents (your skills), shared knowledge, shared tools, and the work product they produce. You direct the HQ; the agents execute.

## The four layers

| Layer | Term | What it holds |
|-------|------|---------------|
| Capabilities | **Skills** | Specialized agents you build for parts of the work — each skill = one agent |
| Context | **Knowledge** | What you and the agents know — about the project, you, the domain |
| Execution | **Tools** | What the agents can *run* — code, scripts, integrations |
| Work product | **Outputs** | What the agents have *produced* — drafts, reports, artifacts |

Each layer compounds independently. Knowledge deepens session by session. Skills accumulate as a roster of specialized agents you can call on. Tools become available to every existing skill the moment they're registered. Outputs form a track record of what the HQ has actually delivered.

## Core principles

1. **Build with need, not ahead of it.** Every skill, tool, and doc is created when there's a real task that requires it. No speculative infrastructure. The first time you do a thing, just do it. The skill comes later — or, if you flag it upfront as a future skill, the first execution becomes its blueprint.

2. **Knowledge is the product.** The HQ's value compounds as context deepens. Every session adds knowledge. Context management is the discipline that makes the compounding work.

3. **Skills define *what*, tools define *how*.** A skill never hardcodes which tools to use — it checks `tools/INDEX.md` at execution time to see what's available. Tools evolve independently. A new tool added today becomes available to every existing skill on its next run, with zero updates to the skill itself.

4. **Pointers over content.** Context files reference where information lives. They don't duplicate it. The agent reads source files on demand. This keeps the always-loaded context small and the on-demand context rich.

5. **The HQ builds itself.** As work happens, patterns emerge. When a task recurs or grows complex, it becomes a new specialized agent (skill). When a domain deepens, it gets its own knowledge doc. The HQ grows organically from real work.

## How it works

- **`CLAUDE.md`** — The spine. Defines the operating presence, the project, communication style, and a pointer index to deeper docs. Includes the Skill Index — the runtime registry of every specialized agent currently in the HQ. Stable, ~100 lines max.
- **`STATE.md`** — Where the project is right now. Current focus, status, priorities. Volatile, capped at 80 lines, updated when you ask.
- **`docs/`** — Deep context. The manifesto (this file), the context update protocol, building guides, project/domain knowledge.
- **`skills/`** — Your specialized agents. Each skill is self-contained: instructions, process, references. Simple skills are a single file. Complex skills are a directory.
- **`tools/`** — Your code. Scripts, API integrations, scrapers, anything executable. `tools/INDEX.md` is the runtime registry skills check.
- **`workspace/`** — All work product. Organized by domain. This is where the agents' outputs live.

## Why this works

Most "AI agent" attempts fail because they try to design the agent's capabilities in advance. They produce frameworks full of speculative skills no one ends up using.

This system inverts that. The first time you do a thing, you just do it. The second time — or the moment you decide it's worth standardizing — the work itself becomes the spec for the skill. Tools are built when the task demands them, and they immediately become part of the runtime that every skill can draw on.

The HQ's competence is shaped by your actual work, not by someone else's guess about what an agent should be able to do.

## Working session, end-to-end

1. Open Claude Code in this directory.
2. The operating presence reads `CLAUDE.md` (always loaded) and `STATE.md` (always loaded).
3. You give it a task.
4. If a matching skill exists, it loads that skill's `SKILL.md` and operates as that specialized agent for the duration of the work.
5. If not, it just does the work — unless you've flagged it as a future skill, in which case it shapes the work deliberately so the skill captures it cleanly.
6. At session end, ask "should we update context?" — the agent loads `docs/CONTEXT-PROTOCOL.md` and proposes specific edits.

That's the whole loop. Everything else is the four layers compounding.
