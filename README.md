# AgyCLI Skill

A dedicated agent skill for operating the local `agy` CLI (formerly the Gemini CLI). This skill provides agents with machine-readable defaults, bounded workflows, and up-to-date documentation on the CLI surface.

## Overview

The AgyCLI skill teaches an AI agent how to interact with the local `agy` CLI safely and effectively. It provides three primary workflows:

- **Headless Mode (`agy -p`)**: For running bounded, one-off prompts with plain text output. Includes guidance on prompt engineering for structured outputs.
- **Interactive Mode (`agy -i`)**: For steering a back-and-forth session using background task management.
- **Plugin Management (`agy plugin`)**: For discovering, installing, and managing plugins.

## Installation

To install this skill for your agent, clone this repository into your agent's skills directory:

```bash
git clone https://github.com/gitguffaw/AgyCLI.git ~/.gemini/config/skills/AgyCLI
```

The agent will automatically discover the `SKILL.md` file and route requests accordingly.

## Structure

- [`SKILL.md`](SKILL.md): The primary entrypoint and routing table for the agent. Includes the legacy `.gemini/` migration protocol.
- [`Workflows/`](Workflows/): Detailed execution contracts for Headless, Interactive, and Plugin tasks.
- [`references/QuickRef.md`](references/QuickRef.md): The verified CLI surface, flags, and facts to prevent the agent from hallucinating nonexistent commands.

## Versioning

This repository tracks the latest capabilities of the `agy` CLI. See the `VERIFIED` stamp in `references/QuickRef.md` to check against your installed version.
