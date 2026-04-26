# Context Update Protocol

Loaded only when the user asks "should we update context?". Not part of the always-loaded spine — kept here so the agent's attention stays on the work itself, and update logic loads precisely when it's needed.

## When to evaluate

| Trigger | Action |
|---------|--------|
| Current focus changed | Update `STATE.md` → Current Focus |
| Status of a system/area changed (shipped, broke, in progress) | Update `STATE.md` → System Status |
| Architectural or strategic decision made | Update the relevant `docs/` file (or create one if the domain just emerged) |
| New skill (specialized agent) was created | Update `CLAUDE.md` → Skill Index, add a row to `QUICKSTART.md` → Slash Commands, ensure a `/<skill-name>` slash command exists in `.claude/commands/` |
| New tool was created | Update `tools/INDEX.md` (skills don't need updating — they discover at runtime) |
| Knowledge about user or domain deepened | Update `docs/PROFILE.md` or `docs/DOMAIN.md` (create from template if first time) |
| Info in `STATE.md` is now outdated | Remove it |
| Domain became complex enough for its own file | Create `docs/<DOMAIN>.md` and add a pointer in `CLAUDE.md` |
| New "common prompt" pattern emerged the user keeps reaching for | Add a row to `QUICKSTART.md` → Common Prompts |

## Rules

- **Never update context files without user request.** Even if you spot something that should be updated mid-work, hold it for the end-of-session prompt.
- **Every entry is a pointer or a decision, not a description.** "Auth: Firebase (chose over Supabase, needed phone auth) → /src/auth/" beats "We use Firebase to handle authentication."
- **Never summarize what can be read from a file.** If the info lives in code or another doc, point to it.
- **STATE.md must stay under 80 lines.** If it's growing, prune or move long content into `docs/`.
- **Be specific when proposing changes.** Quote what to add, what to remove, what to change.

## What makes a good entry

| Bad | Good |
|-----|------|
| `Marketing → docs/MARKETING.md` | `Marketing (positioning, channels, voice) → docs/MARKETING.md` |
| `We use Stripe for payments` | `Payments: Stripe (chose over LemonSqueezy for EU coverage) → /src/payments/` |
| Long paragraph summarizing architecture | One-line pointer: `Architecture (services, deploys, key decisions) → docs/ARCHITECTURE.md` |

The extra few words on a pointer save a file read; long summaries duplicate what already exists elsewhere.

## After evaluation

Present changes as a checklist before writing anything:

```
Context updates:
- [ ] STATE.md: Update current focus to "..."
- [ ] STATE.md: Mark <area> as ✅ Live
- [ ] CLAUDE.md → Skill Index: Add row for new skill <name>
- [ ] QUICKSTART.md → Slash Commands: Add row for /<name>
- [ ] docs/DOMAIN.md: Add decision about <X>
- [ ] No other changes needed
```

Wait for explicit user approval before making any of the changes.

## Edge cases

- **User says "yes update everything"** → still propose the checklist first, get a confirm, then execute.
- **You're unsure whether something rises to a context update** → ask. "I noticed X — worth recording, or one-off?"
- **MEMORY.md or auto-memory holds something system-critical** → propose moving it to the appropriate `docs/` file. Auto-memory is the agent's notebook, not curated context.
