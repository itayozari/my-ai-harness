# Onboarding Flow

Triggered by `/onboard`. Sets up a new harness for the user.

## Goal
Take the user from fresh clone to "ready to work" in five minutes. Capture the project, capture how they want to work, invite (don't require) starter knowledge, explain how the harness actually runs, hand off.

## Principles
- **Sequence, don't batch.** One question at a time.
- **Plain language.** Don't lead with file names. The user doesn't care about `CLAUDE.md` and `STATE.md` — they care about getting set up.
- **Explain through how it works, not abstractions.** No five-part-model lecture upfront — show it via the loop they'll actually use.
- **Don't push for a goal.** The first task they give will be the goal.
- **Generate the minimum.** A starting `CLAUDE.md`, an empty `STATE.md`, and any docs from Q3 if the user shared something. That's it.
- **Mention agents only as a future possibility, in one line.** They're an advanced, optional layer most users won't need at first. Don't go deep — one sentence in the closing explanation is enough.

## The flow

### Open
One short message:

> *"This is your personal AI harness. Three quick questions to set it up, then we get going."*

### Q1 — The project
> *"What's the project? What are you building or working on?"*

One open question. **Don't list examples** — examples narrow the answer instead of opening it. Let the user describe their project in their own words.

If the answer is short or vague, one follow-up: *"A bit more — what is it, who's it for, what stage?"*

### Q2 — How to work together
> *"Anything I should know about you and how you want me to work? Communication style, how much pushback, anything I should never do."*

One question, combines style and boundaries.

### Q3 — Existing knowledge (optional)
> *"Got any context already — docs, notes, anything written down? Drop file paths or paste text. Or skip — we'll accumulate this together over time."*

Three valid responses:
- **File paths** → read and absorb. Save useful pieces under `docs/` with sensible names (ask the user for naming if non-obvious).
- **Pasted text** → save as `docs/<DOMAIN>.md` (ask for the domain name).
- **Skip** → fine, move on. Knowledge grows from real work.

### Set up the core
Write the master definitions silently. Don't make file names central. After writing, give a one-line confirmation:

> *"Set up. Project: \<X\>. Style: \<Y\>. Knowledge: \<recorded what you shared, or starting empty\>."*

What got written:
- `CLAUDE.md` — role, project summary, communication style, pointers updated.
- `STATE.md` — left as the empty template (current focus fills in when work starts).
- `docs/<name>.md` — only if Q3 produced content worth recording.

If the user wants to see what was written, they ask. Don't volunteer a file dump.

### Explain the harness, then how it runs
One short framing line (what this is — like the README opener), then the loop. Keep the whole thing brief — under ~10 lines of dialogue total.

> *"Quick framing: this is a personal harness for your AI — it accumulates context, skills, tools, and outputs around your project. Gets sharper over time because the harness fills up, not because the model changed.*
>
> *How it runs:*
>
> *— You give me a task. We do it.*
>
> *— If you'll repeat it or want it done consistently well, flag it: 'this is going to be a skill.' I'll wrap it as a skill at the end. Once built, you invoke it with `/<skill-name>` — all your skills live in `QUICKSTART.md` so you can see what's available.*
>
> *— As skills accumulate, you can also build agents — optional orchestrations that combine multiple skills into one task. Most projects never need them; mention if you ever want one.*
>
> *— Session end: just say 'should we update context?' — anything worth keeping gets recorded."*

### Hand off
> *"Ready when you are. What do you want to do?"*

That's the close. The first task they give becomes the working goal — let it surface naturally.

## What NOT to do during onboarding

- **Don't list role examples** ("research assistant", "marketing operator", "study partner"). They narrow the user's thinking — they pick from your list instead of describing their actual project.
- **Don't ask the user to articulate a goal** before they have a task in mind. Hand off and let the first task become the goal.
- **Don't lead with file names.** "I'll generate `CLAUDE.md` and `STATE.md`" is meaningless to a non-technical user. Talk about what's being recorded, not where it's stored.
- **Don't lecture about the five-part model.** It comes through naturally in the "how this runs" explanation.
- **Don't mention agents.** Agents are an advanced, optional layer. Introducing them during onboarding adds confusion, not value. They surface later when work actually needs them.
- **Don't create `docs/PROFILE.md` or domain files** unless Q3 produced specific content for them.
- **Don't ask about technical preferences** (stacks, languages, tools) unless the user volunteers them.
