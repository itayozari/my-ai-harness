# workspace/

Where all work product lives. Drafts, reports, dashboards, lead lists, analyses, anything the agent produced for you.

## Conventions

- **Organize by domain.** Create folders that match how you think about your work. Examples: `workspace/research/`, `workspace/contracts/`, `workspace/papers/`, `workspace/campaigns/`. The agent suggests folder names; you decide what fits.
- **Add an `INDEX.md` per subfolder once it has more than ~5 files.** It becomes the catalog of what's there. The skill that produces work in that folder is responsible for keeping the index updated.
- **First deliberate run sets the convention.** When you flag a task as a future skill, the workspace structure produced on that first run becomes the convention every subsequent run inherits. Get it right while attention is on it.

## Interactive outputs

If a deliverable would be more useful as something configurable, explorable, or tweakable (an interactive explorer, a what-if dashboard, a parameter-driven artifact), the agent will suggest the **`playground`** plugin skill — it produces self-contained single-file HTML playgrounds. Don't reach for it by default; only when interactivity is genuinely better than static markdown.

## What does *not* go here

- Source code for tools — that lives in `tools/`.
- Skill definitions — those live in `skills/`.
- Knowledge or reference docs — those live in `docs/`.

If you find yourself wondering whether something belongs here or in `docs/`: outputs go here, knowledge goes there. The line is "did the agent produce this for a specific task" (here) vs "is this a reusable reference the agent reads to do work" (docs).
