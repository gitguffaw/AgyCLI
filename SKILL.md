---
name: AgyCli
description: Operate the local agy CLI (formerly Gemini CLI) with serialized, machine-readable defaults. USE WHEN tasks explicitly require agy CLI OR local agy headless runs OR agy interactive sessions OR agy plugin management.
---

# agy CLI

Operate local `agy` with serialized defaults. Keep command truth in workflows and `references/QuickRef.md`.

## Hard Rules

- Concurrency: `1`
- Delay between invocations: `30s`
- Default headless form: `agy -p "<prompt>"`
- Treat non-zero exit as total failure
- Do not invent model ids; use `agy models` to discover available models

## Default Route

1. Need one bounded text run → `Headless`
2. Need iterative terminal work → `Interactive`
3. Need agy plugin/admin work → `Plugins`

## Workflow Routing

| Workflow | Trigger | File |
|----------|---------|------|
| **Headless** | Need one bounded agy run with text output | `Workflows/Headless.md` |
| **Interactive** | Need iterative agy terminal work, session reuse, or project flows | `Workflows/Interactive.md` |
| **Plugins** | Need agy plugin management (install, import, enable/disable) | `Workflows/Plugins.md` |

## Migration Protocol (gemini → agy)

When encountering legacy `.gemini/` configuration folders in a workspace:
1. Do not delete or overwrite the `.gemini/` folder automatically.
2. Read any necessary configurations or historical state from `.gemini/` if needed.
3. Use the `agy` CLI for all new operations, which natively creates and relies on `.agy/` folders.
4. If explicitly migrating a project, port the legacy configurations to `.agy/` safely, verify the new setup, and only then (if approved) remove the old `.gemini/` directory.

## Files

- `references/QuickRef.md`: verified local CLI surface

## Examples

**Example 1**
```text
Task: "Run agy locally and return one result."
Route: Headless
Entry: agy -p "Summarize the repo"
```

**Example 2**
```text
Task: "Open agy in a resumable terminal session for iterative steering."
Route: Interactive
Entry: agy -i "Inspect the current repo and stay interactive"
```

**Example 3**
```text
Task: "List installed plugins and import plugins from another CLI."
Route: Plugins
Entry: agy plugin list; agy plugin import gemini
```
