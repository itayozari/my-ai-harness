# Tools Index

Runtime registry of tools available to skills. Skills check this file at execution time to discover what they can use.

**The whole point of this file:** add a new tool here once, and every existing skill can use it on its next run with zero updates to the skill itself. That's how skills and tools evolve independently.

## Available tools

| Tool | Path | Purpose | Inputs | Outputs |
|------|------|---------|--------|---------|
| _(none yet)_ | | | | |

## How to register a new tool

1. Build the tool under `tools/<name>/`. Include a `README.md` with purpose, inputs/outputs, how to invoke, dependencies, and failure modes. (See `tools/_template/README.md`.)
2. Add a row to the table above.
3. Done. Every skill that runs after this point can discover and use the tool by reading this file.

See `docs/BUILDING.md` for the full process.
