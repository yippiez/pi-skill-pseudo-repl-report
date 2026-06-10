---
name: html-report
description: >-
  Use when the user asks for an HTML report, screenshot report, before/after UI
  verification, tmux/browser captures, or a clickable artifact to review. Produce
  a polished dark HTML report in /tmp with images, concise findings, and WSL-friendly links.
---

# HTML report skill

Use this skill whenever the user asks to verify visual changes, capture screenshots, compare before/after states, or create a reviewable report.

## Required outcome

Create a self-contained report directory under `/tmp`, usually:

```text
/tmp/<project-or-feature>-report/
  index.html
  *.png
  report.css        # optional; inline CSS is also fine for tiny reports
```

Then reply with:

1. Linux path to `index.html`
2. `file://` URL
3. Windows WSL path when applicable
4. Short list of what was verified

See `OUTPUT_LINK.md` in this skill directory for exact link formats.

## Visual style

Reports should use a dark, compact style matching Pi terminal screenshots:

- page background: `#111`
- card / image background: `#1e1e1e`
- text: `#ddd`
- muted text: `#aaa`
- border: `#444`
- code chips: `#222`
- layout: responsive CSS grid for image comparisons
- headings: short, descriptive, not verbose
- screenshots: bordered, max-width 100%, no distortion

Prefer this structure:

```html
<h1>Feature verification</h1>
<p>Actual tmux/browser screenshots captured after the change.</p>
<ul>
  <li>What changed.</li>
  <li>What the screenshot proves.</li>
</ul>
<div class="grid">
  <section><h2>Before</h2><img src="before.png" /></section>
  <section><h2>After</h2><img src="after.png" /></section>
</div>
```

Use `examples/report.css` as the default CSS for larger reports.

## Screenshot rules

- Prefer **actual UI screenshots**, not fake `printf` output, when the user asks to verify real behavior.
- If a fake/minimal reproduction is used, label it clearly as synthetic.
- For Pi TUI/tmux reports, use the project screenshot script if present, e.g. `scripts/tmux-shot.sh`.
- Capture enough terminal width/height that important text is visible.
- If comparing motion/cursor behavior, make before and after visually distinct.
- If the user says a screenshot is unclear, regenerate it with a better setup.

## Report workflow

1. Make code/config changes.
2. Start an actual app/session in tmux/browser when possible.
3. Drive the UI with keys/clicks/commands.
4. Capture screenshots into `/tmp/<name>-report/`.
5. Write `index.html` referencing local images.
6. Optionally include a short verification transcript in the report.
7. Reply with links and concise notes.

## Naming

Use descriptive report directories:

```text
/tmp/pi-prompt-chain-style-report
/tmp/pi-ui-report
/tmp/<repo>-<feature>-report
```

Use descriptive images:

```text
before.png
after.png
settings-command.png
sent-message-background.png
wrap-before-down.png
wrap-after-down.png
```

## Do not

- Do not only say “verified” without an artifact when the user requested a report.
- Do not hide the report path.
- Do not provide only a Linux path if the user is on Windows/WSL and asked for a clickable link.
- Do not push report artifacts into the repo unless explicitly requested.
