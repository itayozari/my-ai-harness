# Cross-Role Examples

Short vignettes showing how different people set up an HQ around different kinds of projects. Read these to get a feel — none of them are pre-built into the repo. They're the kind of thing you'd grow yourself.

Each example follows the same arc: real work happens → a pattern emerges → it gets captured as a skill (a specialized agent for that slice of the project), with tools and workspace structured along the way.

---

## A research scientist

**Role:** PhD researcher in climate policy.
**Domain:** literature review and synthesis for a multi-paper thesis.

**First few sessions:** uses the agent ad-hoc to summarize papers, compare conflicting findings, draft sections.

**Pattern emerges:** every paper goes through the same evaluation — claim, evidence quality, conflicts with prior work, relevance to thesis chapters.

**Captures it as a skill (`paper-review`):**
- The skill defines the evaluation rubric.
- A tool (`tools/arxiv-fetch/`) gets built to pull paper metadata.
- Workspace convention: `workspace/papers/<paper-slug>/` holds the eval, the source PDF link, the synthesis notes.

**Knowledge layer fills in:** `docs/THESIS.md` captures chapter outlines, central arguments, rejected directions. The agent reads it before any drafting work.

---

## A product manager

**Role:** PM at a B2B SaaS company.
**Domain:** roadmap planning, customer research synthesis, internal comms.

**First few sessions:** processes interview transcripts, drafts PRDs, summarizes Slack threads for status updates.

**Pattern emerges:** customer interviews always need the same treatment — verbatim pain points, jobs-to-be-done framing, severity scoring, feature implications.

**Captures it as a skill (`interview-synthesis`):**
- A tool (`tools/transcript-cleaner/`) strips filler words from raw recordings.
- Workspace convention: `workspace/interviews/<customer>/<date>/` holds the transcript, the synthesis, and the implications.

**Knowledge layer fills in:** `docs/PRODUCT.md` captures the current roadmap, ICP, and recent decisions. Used during PRD drafting and trade-off conversations.

---

## A solo lawyer

**Role:** independent attorney, contract review and drafting.
**Domain:** SaaS B2B contracts, NDAs, employment agreements.

**First few sessions:** flags problematic clauses in NDAs, drafts redlines, explains terms to clients in plain language.

**Pattern emerges:** every contract review hits the same checklist — IP assignment, liability caps, indemnification scope, termination triggers, governing law.

**Captures it as a skill (`contract-review`):**
- A tool (`tools/clause-extractor/`) pulls clauses by category from a PDF.
- Workspace convention: `workspace/contracts/<client>/<contract-name>/` holds the original, the redline, and the client-facing explainer.

**Knowledge layer fills in:** `docs/PRACTICE.md` captures the lawyer's positions on standard issues (e.g., "I push back on uncapped indemnification by default unless the client has insurance"). The agent applies these positions during reviews.

---

## What these have in common

- **Started with real work.** None of them began by designing skills.
- **Skills emerged from patterns**, not predictions.
- **Tools were built when the task demanded them.** Every tool is referenced from at least one skill via `tools/INDEX.md` — none were speculative.
- **Workspace got structured during the first deliberate run**, so every subsequent run inherits the convention without re-deciding.
- **Knowledge accumulates.** The user's domain doc gets richer with every session.

You don't need to follow any of these layouts. They're shape, not blueprint.
