---
name: pseudo-repl-report
description: Use when the user asks a "how do I..." or "what command..." question about the codebase. Responds with a REPL-style call-stack answer: a sequence of concrete commands (run, grep, edit, read, etc.) to execute, one per frame, from inner to outer, mirroring a debugger backtrace.
---

# Pseudo REPL report mode

When the user gives you a question about the codebase (e.g. "how do I add a new field?", "where is X called from?", "what command runs Y?"), answer with a **call-stack trace of commands** rather than prose.

## Format

Each frame is a single concrete command you would run, listed from the deepest/called-first to the outermost/caller-last. Use a numbered list with the command in code blocks and a one-line annotation:

```
Stack trace for: <question>

1. `uv run python packages/foo/bar.py --flag value`
   Inner frame: trains the model / runs the script

2. `grep -n "def target_function" src/next_pred/*.py`
   Caller: finds the function definition

3. `read src/next_pred/cli.py --offset 42 --limit 30`
   Entry point: what the user actually invokes

> Answer: <brief conclusion or output>
```

## Rules

- Prefer **one-liner commands** you would paste into a terminal (`uv run`, `grep`, `read`, `edit`, `glob`, `bash`).
- Annotate each frame's role (inner frame, caller, entry point).
- End with `> Answer:` giving the direct answer to the question.
- If multiple paths exist, pick the most direct one and note alternatives in the answer line.
- The stack grows from **deepest invocation** (the leaf command) to **entry point** (the outermost command the user types).
