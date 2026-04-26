# Building Skills, Agents, and Tools

How real work becomes reusable infrastructure in your harness.

The build flow is **deliberate, not retroactive**. The user flags a task as a future skill (or agent) at the start. The first execution is the blueprint.

```
1. User: "this is going to be a skill — let's do <task>"
2. AI works the task, but consciously:
   - Builds any missing tools (and registers them in tools/INDEX.md)
   - Structures the workspace output the way every future run should follow
   - Notes the steps, decisions, and quality bars being applied
3. At the end, captures all of it into skills/<name>/SKILL.md
   and registers in CLAUDE.md → Skill Index.
```

Why this beats "wait for it to recur, then extract": you don't have to reverse-engineer a pattern from messy history. The first run *is* the spec, written intentionally.

If the user didn't flag it upfront and the work turns complex, the AI should ask once mid-run: *"Want this to become a skill?"*

---

## Building a skill

A skill is a reusable process for a kind of work that repeats.

### When
- The user said it upfront.
- Or the work is recurring and the user asked to capture the pattern.

### Anatomy
```
skills/<name>/
├── SKILL.md      # Instructions: purpose, when to use, principles, process pointer
└── PROCESS.md    # Step-by-step process (only if more than ~5 steps)
```

Simple skills can be a single `SKILL.md` file. Complex skills add reference files (`PROCESS.md`, `EXAMPLES.md`, `RUBRIC.md`, etc.) loaded on-demand.

A skill template lives at `skills/_template/`. Copy, rename, fill in.

### What goes in SKILL.md
- **Purpose** — one paragraph. What the skill does, what "done" looks like.
- **When to use** — the trigger. Specific enough to disambiguate from neighboring skills.
- **Core principles** — 3-7 numbered principles that shape every run. Where the *quality bar* lives.
- **Process** — either inline (if short) or pointer to `PROCESS.md`.
- **Tool check** — explicit instruction: *"Before executing, scan `tools/INDEX.md` for relevant capabilities."*
- **Reference files** — table of any sibling files and what each is for.
- **Storage** — where outputs go in `workspace/`.

### Capturing the first run into a skill — checklist
- [ ] Title and one-line purpose match what the work actually accomplished.
- [ ] "When to use" is specific enough to disambiguate from neighboring tasks.
- [ ] Principles applied during the work are captured (not invented post-hoc).
- [ ] Process matches what was actually done — same steps, same order.
- [ ] Tools used are listed by reference. New tools built are already in `tools/INDEX.md`.
- [ ] Workspace output structure is documented and matches what was produced.
- [ ] Skill is registered in `CLAUDE.md` → Skill Index with a clear trigger.
- [ ] Slash command exists at `.claude/commands/<skill-name>.md`. Use the template at `.claude/commands/_command-template.md`.
- [ ] `QUICKSTART.md` → Slash Commands has a row for the new skill.

Show the user the proposed skill files (and the slash command, and the QUICKSTART update) for approval before writing.

---

## Building an agent (optional, advanced)

An agent is an orchestration — a task definition that combines multiple skills with its own triggers and specialization.

### When to build an agent vs. a skill

Use an **agent** when:
- The task naturally spans multiple skills that need to be coordinated.
- There's specialized competency or quality bar that lives above any single skill.
- The orchestration itself is the reusable thing.

Use a **skill** when:
- The task is a single discipline.
- A single process captures it.

If an "agent" doesn't add anything beyond chaining its skills, you don't need an agent — just put a slash command pointing to the skill (or skills) directly.

### Anatomy
```
agents/<name>/
└── AGENT.md      # Purpose, skills used, triggers, specialization, orchestration
```

An agent template lives at `agents/_template/`.

### What goes in AGENT.md
- **Purpose** — what the agent does, what "done" looks like.
- **Skills it pulls from** — list of skills used and how each is used.
- **Triggers** — slash command, phrase, context.
- **Specialized competency** — what this agent does that goes beyond just chaining its skills.
- **Orchestration** — how the skills get sequenced/combined.
- **Tool check** — same instruction as skills.
- **Storage** — where outputs land in `workspace/`.

### Capturing an agent — checklist
- [ ] Purpose names a kind of task the agent performs.
- [ ] Skills it uses are listed by reference, with how each is used.
- [ ] Specialized competency is real (not just "uses skills A and B"). If it's not, drop the agent and use a slash command directly.
- [ ] Orchestration logic is explicit — sequence, conditions, dependencies.
- [ ] Agent is registered in `CLAUDE.md` → Agent Index.
- [ ] Optional: slash command at `.claude/commands/<agent-name>.md` and a row in `QUICKSTART.md`.

---

## Building a tool

The skill (or the work in front of you) needs a capability that doesn't exist yet — an API client, a scraper, a script, an MCP integration. Build the tool first, then continue the work.

### Anatomy
```
tools/<name>/
├── README.md     # What it does, inputs, outputs, how to invoke, env vars
├── <code files>  # The actual implementation
└── .env.example  # If it needs secrets
```

A tool template lives at `tools/_template/`.

### What goes in `tools/<name>/README.md`
- **Purpose** — one line.
- **Inputs / outputs** — what it expects, what it returns.
- **How to invoke** — exact command, including env-var setup.
- **Dependencies** — anything that needs `npm install`, `pip install`, etc.
- **Failure modes** — what breaks it, how to tell.

### Registering a tool
Add a row to `tools/INDEX.md`:

```
| Tool | Path | Purpose | Inputs | Outputs |
|------|------|---------|--------|---------|
| <name> | `tools/<name>/` | <one line> | <inputs> | <outputs> |
```

Once registered, every existing skill and agent can use this tool on its next run — no skill or agent changes needed. That's the whole point of `tools/INDEX.md`.

---

## When workspace output benefits from interactivity

If the deliverable would be more useful as something the user can configure, explore, or tweak (an interactive explorer, a what-if dashboard, a scoring playground, a parameter-driven artifact), suggest the **`playground`** plugin skill. It produces self-contained single-file HTML artifacts with controls and live preview. Strong fit for many workspace outputs that would otherwise be static markdown.

Don't reach for it by default — only when interactivity is genuinely better than static markdown.

---

## What you should not do

- **Don't build skills, agents, or tools speculatively.** "We might need this someday" is not a reason. Wait for the work.
- **Don't hardcode tool names inside a skill or agent.** They scan `tools/INDEX.md` — the runtime resolves which tool to use.
- **Don't bundle multiple loosely related capabilities into one skill or agent.** Two distinct triggers → two skills (or split into a skill + a wrapping agent).
- **Don't skip workspace structure on the first run.** The first output's folder layout becomes the convention. Get it right while attention is on it.
- **Don't reach for an agent when a skill would do.** The agent layer is optional. Most projects never need it.
