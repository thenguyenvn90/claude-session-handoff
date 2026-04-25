# Contributing to claude-session-handoff

Thanks for your interest in contributing. This project is a Claude Code skill — a single Markdown file (`SKILL.md`) that Claude Code loads to produce structured session handoffs.

## What you can contribute

- **Bug reports** — the skill produces malformed output, misses sections, or doesn't trigger
- **Improvements to SKILL.md** — clearer instructions, better examples, edge case handling
- **README improvements** — clearer install steps, better example output
- **Translations** — adapting the output template for non-English workflows

## Development setup

No build system needed — this repo is pure Markdown.

1. Fork and clone the repo
2. Edit `SKILL.md` or `README.md` directly
3. Test by copying `SKILL.md` to your Claude Code skills directory:
   ```bash
   # macOS / Linux
   cp SKILL.md ~/.claude/skills/session-handoff.md

   # Windows
   copy SKILL.md %USERPROFILE%\.claude\skills\session-handoff.md
   ```
4. Start a new Claude Code session and test the trigger phrases

## Pull request process

1. Fork the repo and create a branch (`fix/section-order`, `feat/add-example`)
2. Make your changes
3. Verify the skill still produces all 7 required sections in the correct order
4. Open a PR with a clear description of what changed and why

## Code of conduct

This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md). By participating, you agree to its terms.

## Questions?

Open an [Issue](https://github.com/thenguyenvn90/claude-session-handoff/issues) — no question is too small.
