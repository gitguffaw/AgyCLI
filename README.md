# AgyCLI Skill

A dedicated interop skill allowing outer AI agents (such as **Claude Code**, **Codex**, or **Grok**) to drive the local `agy` CLI as a secondary coding surface. 

This skill provides those agents with machine-readable defaults, bounded workflows, and up-to-date documentation on the `agy` CLI surface, preventing hallucinations and ensuring safe execution.

## Overview

When an outer agent needs to delegate a task to `agy` (e.g., to utilize a specific model, run in a sandboxed terminal, or manage agy plugins), it reads this skill to understand the correct syntax.

The skill provides three primary workflows:
- **Headless Mode (`agy -p`)**: For running bounded, one-off prompts with plain text output. Includes guidance on prompt engineering for structured outputs.
- **Interactive Mode (`agy -i`)**: For steering a back-and-forth session using background task management.
- **Plugin Management (`agy plugin`)**: For discovering, installing, and managing plugins.

## Installation

To equip your outer agent with the ability to drive `agy`, clone this repository and symlink it into the respective agent's skills directory.

```bash
# 1. Clone the repository to a central location
git clone https://github.com/gitguffaw/AgyCLI.git ~/.agy-skills/AgyCLI

# 2. Install for Claude Code
ln -s ~/.agy-skills/AgyCLI ~/.claude/skills/AgyCLI

# 3. Install for Codex
ln -s ~/.agy-skills/AgyCLI ~/.codex/skills/AgyCLI

# 4. Install for Grok
ln -s ~/.agy-skills/AgyCLI ~/.grok/skills/AgyCLI

# 5. Install for Antigravity
ln -s ~/.agy-skills/AgyCLI ~/.gemini/config/skills/AgyCLI
```

## Structure

- [`SKILL.md`](SKILL.md): The primary entrypoint and routing table for the outer agent. Includes the legacy `.gemini/` migration protocol.
- [`Workflows/`](Workflows/): Detailed execution contracts for Headless, Interactive, and Plugin tasks.
- [`references/QuickRef.md`](references/QuickRef.md): The verified CLI surface, flags, and facts to prevent the agent from hallucinating nonexistent commands.

## Versioning

This repository tracks the latest capabilities of the `agy` CLI. See the `VERIFIED` stamp in `references/QuickRef.md` to check against the currently supported version.
