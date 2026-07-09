# Plugins

Use when the task is about managing agy plugins, not running a model prompt.

## List

```bash
agy plugin list
```

## Import

Import plugins from another CLI's configuration:

```bash
agy plugin import gemini
agy plugin import claude
```

## Install / Uninstall

```bash
agy plugin install <target>
agy plugin install <plugin>@<marketplace>
agy plugin uninstall <name>
```

## Enable / Disable

```bash
agy plugin enable <name>
agy plugin disable <name>
```

## Validate

```bash
agy plugin validate <path>
```

## Marketplace Link

```bash
agy plugin link <marketplace> <target>
```

## Facts

- The `plugin` subcommand replaces `gemini skills`, `gemini extensions`, `gemini hooks`, and `gemini mcp`
- `agy plugin import gemini` migrates plugins from a prior Gemini CLI installation
- `agy plugin import claude` migrates from Claude CLI configuration
- Keep agy CLI surface docs centralized in `../references/QuickRef.md`
