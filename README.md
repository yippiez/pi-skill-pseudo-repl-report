# pi-skill-html-report

Standalone Pi skill package for creating polished HTML reports with screenshots, verification notes, and clickable WSL/Windows links.

The included `html-report` skill is for tasks where the user asks to verify UI/terminal changes, produce before/after screenshots, or save a reviewable report in `/tmp`.

## Includes

- `skills/html-report/SKILL.md` — main report workflow and style rules.
- `skills/html-report/OUTPUT_LINK.md` — how to present Linux, `file://`, and Windows WSL links.
- `skills/html-report/examples/report.css` — reusable dark report CSS.
- `skills/html-report/examples/index.html` — minimal report template.

## Install from Git

```bash
pi install git:github.com/yippiez/pi-skill-html-report
```

Local/project install:

```bash
pi install -l git:github.com/yippiez/pi-skill-html-report
```

## Package layout

```text
skills/html-report/SKILL.md
skills/html-report/OUTPUT_LINK.md
skills/html-report/examples/report.css
skills/html-report/examples/index.html
package.json
README.md
```
