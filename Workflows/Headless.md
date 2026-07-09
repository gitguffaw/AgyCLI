# Headless

Use for one bounded agy invocation with text output.

## Command

```bash
agy -p "<prompt>"
```

Pin a known model only when the caller already knows the model id:

```bash
agy --model <model> -p "<prompt>"
```

## Execution Contract

- Run one agy process at a time.
- Sleep `30s` before the next agy invocation.
- Default timeout: `5m` (controlled by `--print-timeout`).
- Override timeout when a shorter budget is needed: `agy --print-timeout 2m -p "<prompt>"`.
- Retry exactly once after `30s` on command failure or timeout.
- If the caller already knows a stable model id, prefer explicit `--model`; do not guess ids.

## Output Contract & Prompt Engineering

- Success output is plain text printed to stdout.
- No structured JSON output mode exists. To enforce structured responses, use strong prompt engineering (e.g., instructing the model to output ONLY valid JSON without markdown code blocks or conversational text). Parse the plain text output as-is or post-process downstream.
- Non-zero exit invalidates the run.
- Return stderr diagnostics on failure.
- If the first attempt fails and the second attempt fails, stop.

## Unknown Model Discovery

If the required model ID is unknown:
1. Run `agy models` (in a separate step) to discover available model IDs.
2. Once the valid ID is found, launch the headless session with `agy --model <discovered_id> -p "<prompt>"`
