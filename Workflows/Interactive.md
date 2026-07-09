# Interactive

Use for iterative steering, live tool use, or session reuse.

## Primary Entry

```bash
agy
agy "<seed prompt>"
agy -i "<prompt>"
```

## Session Control

```bash
agy -c
agy --continue
agy --conversation <id>
agy --new-project
agy --project <id>
```

## High-Value Flags

- `--model`                 Override model for this session
- `--sandbox`               Run with terminal restrictions
- `--add-dir`               Add extra directories to the workspace
- `--dangerously-skip-permissions`  Auto-approve tool permissions
- `--log-file`              Override log file path

## Agent Interaction

When orchestrating an interactive `agy` session, an AI agent must manage the background process using task management tools:
- Use `manage_task send_input` to respond to interactive prompts, supply context, or steer the session.
- Do not poll; the system will automatically notify you with output from the background process, or you can check status via `manage_task status`.

## Unknown Model Discovery

If the required model ID is unknown:
1. Run `agy models` (in a headless `run_command` or background task) to discover available model IDs.
2. Once the valid ID is found, launch the interactive session with `agy --model <discovered_id> ...`

## Routing Rules

- Prefer plain `agy` or `agy -i` when the run needs back-and-forth steering.
- Prefer `Headless` instead when downstream code must consume one final text output.
- Keep interactive agy work serialized; do not fan out multiple agy sessions for the same task.
- If a model is known, add `--model <model>`; do not guess ids. If unknown, follow the discovery flow above.
