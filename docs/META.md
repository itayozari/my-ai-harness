# What Is my-ai-harness

A personal harness for any AI model — a structured workspace where context, skills, tools, and outputs accumulate around one project, making whatever AI you use meaningfully better at *your* specific work.

This particular implementation is wired for Claude Code (via `.claude/` and the `CLAUDE.md` filename convention). The methodology is model-agnostic — adapt the wiring if you use a different tool.

## What lives here

| Part | What it holds |
|------|---------------|
| **Knowledge** | What the AI knows — about you, the project, the domain |
| **Skills** | Reusable processes for kinds of work that repeat |
| **Tools** | Code, scripts, integrations the AI can run |
| **Outputs** | What the AI has produced — drafts, reports, artifacts |
| **Agents** *(optional)* | Task definitions that combine multiple skills with their own triggers and specialization |

The first four are the harness itself. Agents are an optional orchestration layer on top — many users will never need them. Skills cover most of what an AI assistant should do well; agents are for when work needs to coordinate several skills as a single unit.

## Core principles

1. **Build with need, not ahead of it.** Every skill, agent, tool, and doc is created when there's a real task that requires it. No speculative infrastructure. The first time you do a thing, just do it. The skill comes later — or, if you flag it upfront, the first execution becomes its blueprint.

2. **Knowledge is the product.** The harness's value compounds as context deepens. Every session adds knowledge. Context management is the discipline that makes the compounding work.

3. **Skills define *what*, tools define *how*.** A skill never hardcodes which tools to use — it checks `tools/INDEX.md` at execution time. Tools evolve independently. A new tool added today becomes available to every existing skill on its next run, with zero updates to the skill itself. The same applies to agents.

4. **Pointers over content.** Context files reference where information lives. They don't duplicate it. The AI reads source files on demand. This keeps always-loaded context small and on-demand context rich.

5. **The harness builds itself.** As work happens, patterns emerge. When a task recurs or grows complex, it becomes a skill. When several skills need to be coordinated for a kind of task, that coordination becomes an agent. When a domain deepens, it gets its own knowledge doc.

## How it works

- **`CLAUDE.md`** — The spine. The AI's instructions, the project, communication style, the Skill and Agent indexes, pointers to deeper docs. Stable, ~120 lines max.
- **`STATE.md`** — Where the project is right now. Current focus, status, priorities. Volatile, capped at 80 lines, updated when you ask.
- **`docs/`** — Deep context. The manifesto (this file), the context update protocol, building guides, project/domain knowledge.
- **`skills/`** — Your reusable processes. Each skill is self-contained: instructions, process, references.
- **`agents/`** — *(optional)* Your orchestrations. Each agent definition combines skills with triggers and specialization.
- **`tools/`** — Your code. Scripts, API integrations, scrapers, anything executable. `tools/INDEX.md` is the runtime registry skills and agents check.
- **`workspace/`** — All work product. Organized by domain.

## Why this works

Most AI usage resets every session. This one compounds.

You don't pre-design capabilities. You do real work. When something matters enough to standardize, you flag it — the harness captures it as you do it. Tools come online when the task demands them and are immediately available everywhere. Knowledge deepens via a simple update protocol you trigger at session end.

The AI's effective competence at *your* work is shaped by your actual work, not by anyone else's guess at what an AI assistant should be able to do.

## Working session, end-to-end

1. Open Claude Code in this directory.
2. The AI reads `CLAUDE.md` (always loaded) and `STATE.md` (always loaded).
3. You give it a task.
4. If a matching skill or agent exists, it loads and follows it. Otherwise it just does the work — unless you've flagged it as a future skill, in which case it shapes the work deliberately so the skill captures it cleanly.
5. At session end, ask "should we update context?" — the AI loads `docs/CONTEXT-PROTOCOL.md` and proposes specific edits.

That's the whole loop. Everything else is the parts compounding.
