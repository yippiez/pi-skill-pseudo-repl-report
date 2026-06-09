# pi-skill-pseudo-repl-report

Standalone Pi skill package for REPL-style pipeline/report answers.

The included `pseudo-repl-report` skill makes the agent answer codebase questions as a call-stack of concrete commands, ending with a short direct answer.

## Includes

- `skills/pseudo-repl-report/SKILL.md` — REPL call-stack answer format and rules.

## Install from Git

Global install:

```bash
pi install git:github.com/yippiez/pi-skill-pseudo-repl-report
```

Local/project install:

```bash
pi install -l git:github.com/yippiez/pi-skill-pseudo-repl-report
```

## Package layout

```text
skills/pseudo-repl-report/SKILL.md
package.json
README.md
```
