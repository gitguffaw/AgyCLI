# agy CLI Quick Reference

VERIFIED:
- `agy 1.0.16`
- `2026-07-08`

PRIMARY ENTRYPOINTS:
- `agy`
- `agy -i "<prompt>"`
- `agy -p "<prompt>"`

TOP-LEVEL FLAGS:
- `--add-dir`               Add a directory to the workspace (repeatable)
- `-c`, `--continue`        Continue the most recent conversation
- `--conversation`          Resume a previous conversation by ID
- `--dangerously-skip-permissions`  Auto-approve all tool permission requests
- `-i`, `--prompt-interactive`      Run an initial prompt interactively
- `--log-file`              Override CLI log file path
- `--model`                 Model for the current CLI session
- `--new-project`           Create a new project for this session
- `-p`, `--print`           Run a single prompt non-interactively and print the response
- `--print-timeout`         Timeout for print mode wait (default 5m)
- `--project`               Project ID for the current CLI session
- `--prompt`                Alias for --print
- `--sandbox`               Run in a sandbox with terminal restrictions enabled

SUBCOMMANDS:
- `agy changelog`           Show changelog and release notes
- `agy help`                Show help for subcommands
- `agy install`             Configure environment paths and shell settings
- `agy models`              List available models
- `agy plugin`              Manage plugins (install, uninstall, list, enable, disable)
- `agy plugins`             Alias for plugin
- `agy update`              Update CLI

PLUGIN COMMANDS:
- `agy plugin list`                  List imported plugins
- `agy plugin import [source]`       Import plugins from gemini or claude
- `agy plugin install <target>`      Install a plugin (supports plugin@marketplace)
- `agy plugin uninstall <name>`      Uninstall a plugin
- `agy plugin enable <name>`         Enable a plugin
- `agy plugin disable <name>`        Disable a plugin
- `agy plugin validate [path]`       Validate a plugin
- `agy plugin link <mp> <target>`    Generate link to a marketplace

HEADLESS FACTS:
- Canonical form: `agy -p "<prompt>"`
- `-p` runs non-interactively and prints the response as plain text
- `--print-timeout` controls timeout (default 5m)
- Treat non-zero exit as invalid
- Retry once after `30s` on command failure or timeout

SESSION MANAGEMENT:
- `--continue` / `-c`       Resume the most recent conversation
- `--conversation <id>`     Resume a specific conversation by ID
- `--project <id>`          Use a specific project
- `--new-project`           Create a new project for this session

RUNTIME RULES:
- agy concurrency: `1`
- Minimum spacing between invocations: `30s`

AVAILABLE MODELS (as of verification date):
- Gemini 3.5 Flash (Low/Medium/High)
- Gemini 3.1 Pro (Low/High)
- Claude Sonnet 4.6 (Thinking)
- Claude Opus 4.6 (Thinking)
- GPT-OSS 120B (Medium)

MIGRATION NOTES (gemini → agy):
- `gemini` binary no longer exists; use `agy`
- `-o json` / `--output-format` removed; `-p` returns plain text
- `skills`, `extensions`, `hooks`, `mcp` subcommands removed; use `plugin`
- `--worktree`, `--yolo`, `--approval-mode` removed
- `--resume` / `--list-sessions` replaced by `--continue` / `--conversation`
- `.gemini/` project directories may still exist but `agy` uses `.agy/`
