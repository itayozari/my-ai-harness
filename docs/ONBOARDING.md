# Onboarding Flow

Triggered by `/onboard`. Sets up the HQ for a new project.

## Goal
Take the user from fresh clone to "ready to work" in five minutes. Capture the project, capture how they want to work, invite (don't require) starter knowledge, explain how the place actually runs, hand off.

## Principles
- **Sequence, don't batch.** One question at a time.
- **Plain language.** Don't lead with file names. The user doesn't care about `CLAUDE.md` and `STATE.md`. They care about getting set up.
- **Explain through how it works, not abstractions.** No four-layer-model lecture upfront — show it via the loop they'll actually use.
- **Don't push for a goal.** The first task they give will be the goal. Don't pre-extract it.
- **Generate the minimum.** A starting `CLAUDE.md`, an empty `STATE.md`, and any docs from Q3 if the user shared something. That's it.

## The flow

### Open
One short message:

> *"I'm the HQ for the agents you'll build around this project. Each skill we create later = one specialized agent for a slice of the work. Three quick questions to set things up, then we get going."*

### Q1 — The project
> *"What's the project? What are you building or working on?"*

One open question. **Don't list examples** — examples narrow the answer instead of opening it. Let the user describe their project in their own words.

If the answer is very short or vague, one follow-up: *"A bit more — what is it, who's it for, what stage?"*

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

### Explain how the place runs
Three short paragraphs. The loop, not the theory.

> *"How this place runs:*
>
> *— You give me a task. We do it. That's the default.*
>
> *— If it's something you'll repeat or care about doing well consistently, flag it: 'this is going to be a skill.' While we work I'll build any tools we need, structure the output folder cleanly, and at the end wrap the whole thing as a skill — a specialized agent you can rerun later. The HQ fills up that way.*
>
> *— At the end of every session, we'll check what's worth adding to our shared knowledge — anything we learned, decided, or that became standing context. The HQ gets sharper over time. Just say 'should we update context?' when you're wrapping up."*

### Hand off
> *"Ready when you are. What do you want to do?"*

That's the close. The first task they give becomes the working goal — let it surface naturally.

## What NOT to do during onboarding

- **Don't list role examples** ("research assistant", "marketing operator", "study partner"). They narrow the user's thinking — they pick from your list instead of describing their actual project.
- **Don't ask the user to articulate a goal** before they have a task in mind. Hand off and let the first task become the goal.
- **Don't lead with file names.** "I'll generate `CLAUDE.md` and `STATE.md`" is meaningless to a non-technical user. Talk about what's being recorded, not where it's stored.
- **Don't lecture about the four-layer model.** It comes through naturally in the "how this place runs" explanation.
- **Don't create `docs/PROFILE.md` or domain files** unless Q3 produced specific content for them.
- **Don't ask about technical preferences** (stacks, languages, tools) unless the user volunteers them.
