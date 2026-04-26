<!--
Tool template. Copy this folder to `tools/<your-tool-name>/`,
fill it in, and register the tool in `tools/INDEX.md`.

Delete every <placeholder> and every <!-- comment block --> before saving.
-->
# <Tool Name>

## Purpose
<One line. What this tool does and why it exists.>

## Inputs
<What the tool expects. Be precise — names, types, formats.>

- `<input-name>` — <type> — <description>

## Outputs
<What the tool returns or produces. File path, JSON shape, stdout, etc.>

- `<output-name>` — <type> — <description>

## How to invoke
<The exact command. Include any environment variables that must be set.>

```bash
<command here>
```

## Dependencies
<Anything that must be installed for this tool to run. Versions if relevant.>

- <dependency>

## Configuration
<Env vars, config files, API keys. If secrets are needed, also ship a `.env.example`.>

| Variable | Purpose | Required |
|----------|---------|----------|
| `<VAR_NAME>` | <what it's for> | <yes / no> |

## Failure modes
<What breaks this tool. How to recognize the failure. What to do about it.>

- **<Failure type>.** <Symptom. Recovery.>

## Notes
<Optional. Edge cases, performance characteristics, known limitations.>
