---
name: AgyCli
version: 1.0.0
description: Operate the local agy CLI with serialized, machine-readable defaults. USE WHEN tasks explicitly require agy CLI OR local agy headless runs OR agy interactive sessions OR configuring Google Antigravity customizations.
---

# agy CLI

Operate local `agy` (Google Antigravity CLI). This skill helps you drive the CLI effectively as a sub-agent or secondary coding surface.

## Execution Routes

1. **Headless (`agy -p`)**: Use for one bounded text run.
   - Example: `agy -p "Summarize the repo"`
   - Output is plain text. Treat non-zero exit as failure.
   - Run serially. Do not fan out multiple agy processes.

2. **Interactive (`agy -i`)**: Use for iterative terminal steering.
   - Example: `agy -i "Inspect the repo and stay interactive"`
   - You must manage this as a background task. Use `manage_task send_input` to steer.

3. **Customizations (Skills, Rules, Hooks, MCP, Plugins)**: Use for configuring the agent's behavior.
   - Antigravity supports a rich customization system (Skills, Rules, Hooks, MCP Servers). 
   - **Important**: Configurations live in `.agents/` (workspace-level) or `~/.gemini/config/` (global machine-level).
   - Global CLI settings live in `~/.gemini/antigravity-cli/settings.json`.
   - *Do not attempt to migrate configurations to `.agy/` (this is a deprecated/hallucinated path).*

## CLI Command Reference

For a full list of CLI flags, subcommands, and available models, read the verified reference:
[references/QuickRef.md](./references/QuickRef.md)

## Hard Rules

- Concurrency: `1` (Do not run multiple `agy` instances in parallel)
- Delay between invocations: `30s`
- Default headless form: `agy -p "<prompt>"`
- Do not invent model ids; use `agy models` to discover available models.
