# claude-session-handoff

[![CI](https://github.com/thenguyenvn90/claude-session-handoff/actions/workflows/ci.yml/badge.svg)](https://github.com/thenguyenvn90/claude-session-handoff/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/github/v/release/thenguyenvn90/claude-session-handoff)](https://github.com/thenguyenvn90/claude-session-handoff/releases)

> **Credit & origin:** This skill is **created by [Nate Herk](https://www.youtube.com/@NateHerkelman)** (AI Automation Society, 752K YouTube subscribers). Original distribution: **[Nate's Skool community post](https://www.skool.com/ai-automation-society/new-video-how-to-never-hit-your-claude-session-limit-again?p=f49317ee)** (free tier, no credit card required). This GitHub repo is a **public mirror** to make the skill accessible via `git clone` / `curl` for developers who prefer GitHub workflow, with full attribution preserved.
>
> 👉 If you find this skill useful, **support the original author**: join [Nate's free Skool community](https://www.skool.com/ai-automation-society) for the full PDF guide "How to Never Hit Your Claude Limit Again" + video walkthrough + community discussion.

---

A Claude Code skill that produces a structured end-of-session handoff so you can `/clear` context without losing continuity. The next agent picks up by reading the summary alone — no files written, no memory updated.

## What it does

Say **"session handoff"** and Claude produces a chat summary covering:

- What shipped this session (decisions + absolute file paths)
- Key files the next agent should read first
- Running state (background processes, dev servers, open branches)
- How to verify things still work
- Deferred items and open questions
- Single "pick up here" line for the next agent

## Install

Two paths — pick whichever fits your workflow:

### Path 1: Get it from Nate Herk's Skool (recommended)

Visit **[Nate's Skool post](https://www.skool.com/ai-automation-society/new-video-how-to-never-hit-your-claude-session-limit-again?p=f49317ee)** (free tier, no credit card), download the PDF guide, copy the skill template, paste into `~/.claude/skills/session-handoff.md`.

You'll get the full PDF guide "How to Never Hit Your Claude Limit Again" with token economy explanation, context rot deep-dive, and 10 GitHub frameworks for 60-90% token savings.

### Path 2: This GitHub mirror (fast install)

Copy `SKILL.md` to your Claude Code skills directory:

```bash
# macOS / Linux
cp SKILL.md ~/.claude/skills/session-handoff.md

# Windows (PowerShell)
Copy-Item SKILL.md "$env:USERPROFILE\.claude\skills\session-handoff.md"
```

Or download single file directly without cloning:

```bash
curl -o ~/.claude/skills/session-handoff.md \
  https://raw.githubusercontent.com/thenguyenvn90/claude-session-handoff/master/SKILL.md
```

Then start a new Claude Code session. The skill activates automatically on trigger phrases.

## Usage

At any point during a session, just say:

```
session handoff
```

or `wrap up session` / `hand off` / `let's wrap up`. Claude produces the handoff in chat. Paste it into the next session's first message — done.

## Tutorial

For a full walkthrough in Vietnamese with comparison of 9 session handoff implementations, 5 production triggers, customization patterns, and dual-tool (Claude Code + Codex CLI) workflow, see:

📖 **[Session Handoff Claude Code: Skill Tiết Kiệm Context 2026](https://ongboit.com/session-handoff-claude-code/)** (Vietnamese)

The tutorial covers:
- 8 implementation comparison matrix (Nate's skill + 7 alternatives)
- When to trigger handoff (5 production scenarios)
- Customization for Vietnamese trigger phrases and cost tracking
- Anti-pattern: why you should pick 1 skill, not stack multiple
- Cross-tool handoff workflow (Claude Code → Codex CLI)
- 3 sharp edges from production testing (47 PRs measured)

## Example output

```
# Session Handoff — merged token-tracker article and published to WP #5499

## Where it started
User asked to merge two overlapping articles into one 14-repo guide covering
both token reduction and token tracking. Post #5499 was scheduled for the next
day so the update had to land before then.

## Decisions locked + what shipped
- Merged 14 repos / 5 groups — /home/alice/project/articles/blog.md
- Slug changed: github-repos-token-claude-code -> claude-code-token-tracker (WP #5499)
- RankMath 5 focus keywords set
- Backlink in post #3626 patched to new slug

## Key files for next session
- `/home/alice/project/articles/ongboit.com/claude-code-token-tracker/brief.md` — article outline
- Plan file: `~/.claude/plans/snoopy-nibbling-tome.md`
- Memory files touched: none this session

## Running state
- Background processes: none
- Dev servers / ports: none
- Open worktrees / branches: none

## Verification — how to confirm things still work
- `curl -s https://site.com/wp-json/wp/v2/posts/5499 | jq .slug` — should return "claude-code-token-tracker"

## Deferred + open questions
- Deferred: second section image for H2 #6 — ng-image not run yet
- Open: next article topic not confirmed yet

## Pick up here
Run /ng-research "claude code web" to start the next article in the queue.
```

## Why chat-only?

Writing the handoff to a file creates a management problem: where does it live, who reads it, does it get stale. In chat the user sees it immediately, pastes the relevant parts into the next session's first message, and the next agent starts with full context. No file management, no stale handoffs accumulating.

## Why fixed structure?

Every handoff has the same 7 sections in the same order. A fresh agent can scan for `## Pick up here` in under a second. Structure stability is the whole point — if sections appear sometimes and not others, the next agent has to read everything to know what's missing.

## Contributing

PRs welcome for:
- Additional trigger phrases (especially non-English: Vietnamese, Spanish, Japanese)
- Output template improvements
- Worked examples for different domains (data science, devops, web dev)
- Documentation translations

See [CONTRIBUTING.md](CONTRIBUTING.md) for details. Note: contributions stay attribution-preserved to the original author (Nate Herk) per the credit policy at the top of this README.

## License

MIT — but please preserve the credit to Nate Herk in any fork or derivative work. The skill design and template structure are Nate's original work; this repo just provides public mirror access.
