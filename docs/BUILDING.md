# Building Skills and Tools

How real work becomes reusable infrastructure. Two halves of the same loop: skills capture *what* the agent does, tools capture *how*.

## The core method (read this first)

The build flow is **deliberate, not retroactive**. The user flags a task as a future skill at the start. The first execution is the blueprint.

```
1. User: "this is going to be a skill — let's do <task>"
2. Agent works the task, but consciously:
   - Builds any missing tools (and registers them in tools/INDEX.md)
   - Structures the workspace output the way every future run should follow
   - Notes the steps, decisions, and quality bars being applied
3. At the end, agent captures all of it into skills/<name>/SKILL.md
   and registers in CLAUDE.md → Skill Index.
```

Why this beats "wait for it to recur, then extract": you don't have to reverse-engineer a pattern from messy history. The first run *is* the spec, written intentionally.

If the user didn't flag it upfront and the work turns complex, the agent should ask once mid-run: *"Want this to become a skill? If so I'll be more deliberate about tools and workspace structure as we continue."*

---

## Building a skill

### When
- The user said it upfront.
- Or the work is recurring and the user asked to capture the pattern.

### Anatomy of a skill
Every skill is a folder under `skills/`:

```
skills/<name>/
├── SKILL.md      # Instructions: what it does, when to use, principles, process pointer
└── PROCESS.md    # Step-by-step process (only if the skill has more than ~5 steps)
```

Simple skills can be a single `SKILL.md` file. Complex skills add reference files (`PROCESS.md`, `EXAMPLES.md`, `RUBRIC.md`, etc.) loaded on-demand.

A skill template lives at `skills/_template/`. Copy it, rename, fill it in.

### What goes in SKILL.md
- **Purpose** — one paragraph. What the skill does, what "done" looks like.
- **When to use** — the trigger. Be specific enough that the agent picks the right skill in future sessions.
- **Core principles** — 3-7 numbered principles that shape every run. Where the *quality bar* lives.
- **Process** — either inline (if short) or pointer to `PROCESS.md`.
- **Tool check** — explicit instruction: *"Before executing, scan `tools/INDEX.md` for relevant capabilities."* This is what makes runtime tool discovery work.
- **Reference files** — table of any sibling files and what each is for.
- **Storage** — where outputs go in `workspace/`.

### Capturing the first run into a skill — checklist
Once the work is done, the agent writes the skill from what just happened:

- [ ] Title and one-line purpose match what the work actually accomplished.
- [ ] "When to use" is specific enough to disambiguate from neighboring tasks.
- [ ] The principles you applied during the work are captured (not invented post-hoc).
- [ ] The process matches what was actually done — same steps, same order.
- [ ] Tools used are listed by reference (not duplicated). If new tools were built, they're already in `tools/INDEX.md`.
- [ ] Workspace output structure is documented and matches what was produced.
- [ ] Skill is registered in `CLAUDE.md` → Skill Index with a clear trigger.
- [ ] Slash command exists at `.claude/commands/<skill-name>.md` so the user can invoke the skill with `/<skill-name>`. Use the template at `.claude/commands/_command-template.md` — it's a thin trigger that points at `skills/<skill-name>/SKILL.md`.
- [ ] `QUICKSTART.md` → Slash Commands has a row for the new skill, so the project owner sees it in their day-to-day reference.

Show the user the proposed skill files (and the slash command, and the QUICKSTART update) for approval before writing.

---

## Building a tool

### When
The skill (or the work in front of you) needs a capability that doesn't exist yet — an API client, a scraper, a script, an MCP integration. Build the tool first, then continue the work.

### Anatomy of a tool
Each tool gets a folder under `tools/`:

```
tools/<name>/
├── README.md     # What it does, inputs, outputs, how to invoke, env vars needed
├── <code files>  # The actual implementation
└── .env.example  # If it needs secrets
```

A tool template lives at `tools/_template/`. Copy it, fill it in.

### What goes in `tools/<name>/README.md`
- **Purpose** — one line.
- **Inputs / outputs** — what it expects, what it returns.
- **How to invoke** — the exact command, including env-var setup.
- **Dependencies** — anything that needs `npm install`, `pip install`, etc.
- **Failure modes** — what breaks it, how to tell.

### Registering a tool
Add a row to `tools/INDEX.md`:

```
| Tool | Path | Purpose | Inputs | Outputs |
|------|------|---------|--------|---------|
| <name> | `tools/<name>/` | <one line> | <inputs> | <outputs> |
```

Once registered, every existing skill can use this tool on its next run — no skill changes needed. That's the whole point of `tools/INDEX.md`.

---

## When workspace output benefits from interactivity

If the deliverable would be more useful as something the user can configure, explore, or tweak (an interactive explorer, a what-if dashboard, a scoring playground, a parameter-driven tool), suggest the **`playground`** plugin skill. It produces self-contained single-file HTML artifacts with controls and live preview. Strong fit for many workspace outputs that would otherwise be static markdown.

Don't reach for it by default — only when the deliverable is genuinely better as an interactive artifact.

---

## What you should not do

- **Don't build skills speculatively.** "We might need a skill for X someday" is not a reason. Wait for the work.
- **Don't hardcode tool names inside a skill.** The skill says "scan `tools/INDEX.md`" — the runtime resolves which tool to use.
- **Don't bundle multiple loosely related capabilities into one skill.** Two distinct triggers → two skills.
- **Don't skip workspace structure on the first run.** The first output's folder layout becomes the convention. Get it right while the user is paying attention.
