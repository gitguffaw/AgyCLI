# Quick Reference: Agy CLI Surface

**VERIFIED AGAINST**: Google Antigravity (AGY) CLI latest docs

## Base Commands

- `agy`                   Launch interactive agent session (TUI)
- `agy -p <prompt>`         Run a single headless prompt, print to stdout, and exit
- `agy -i <prompt>`         Run a prompt and drop into an interactive session
- `agy models`              List available models
- `agy plugin`              Manage packaged plugins (install, uninstall, list, enable, disable)
- `agy update`              Update CLI

## Headless Contract (`agy -p`)
- Canonical form: `agy -p "<prompt>"`
- `--print-timeout` controls timeout (default 5m)
- Treat non-zero exit as invalid. Retry once after `30s` on failure.
- No structured JSON output mode exists (`-o json` was removed). Use strong prompt engineering if you need JSON text.

## Session Management
- `--continue` / `-c`       Resume the most recent conversation
- `--conversation <id>`     Resume a specific conversation by ID
- `--project <id>`          Use a specific project
- `--new-project`           Create a new project for this session

## TUI Flags (Interactive)
- `--model <id>`            Override model for this session
- `--sandbox`               Run with terminal restrictions
- `--add-dir`               Add extra directories to the workspace
- `--dangerously-skip-permissions`  Auto-approve tool permissions

## Available Models
- Run `agy models` to fetch the current list dynamically.
- Known common ids: `Gemini 3.5 Flash`, `Gemini 3.1 Pro`, `Claude Sonnet 3.5` (Note: do not hallucinate versions, verify via CLI).

## Customization System (Skills, Rules, Hooks, MCP)
While the CLI provides a `plugin` subcommand for packaging, the underlying customization system uses standard directories:
- **Project Scope**: `.agents/` (or `.agent/`, `_agents/`, `_agent/`) at the repo root.
- **Rules**: `GEMINI.md`, `AGENTS.md`, or `.agents/rules/*.md`.
- **Skills**: `.agents/skills/<name>/SKILL.md`.
- **Hooks**: `hooks.json`.
- **MCP Servers**: `mcp_config.json`.
- **Global Settings**: `~/.gemini/config/` (global customizations) and `~/.gemini/antigravity-cli/settings.json` (CLI settings).

**Important**: The `gemini` binary was replaced by `agy`, but the configuration directory `~/.gemini/` is **still correct and active**. Do not migrate `.gemini/` to `.agy/`.
