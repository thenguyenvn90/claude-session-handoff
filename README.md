# claude-session-handoff

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

Copy `SKILL.md` to your Claude Code skills directory:

```bash
# macOS / Linux
cp SKILL.md ~/.claude/skills/session-handoff.md

# Windows (PowerShell)
Copy-Item SKILL.md "$env:USERPROFILE\.claude\skills\session-handoff.md"
```

Then start a new Claude Code session. The skill activates automatically on trigger phrases.

## Usage

At any point during a session, just say:

```
session handoff
```

or `wrap up session` / `hand off` / `let's wrap up`. Claude produces the handoff in chat. Paste it into the next session's first message — done.

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

## License

MIT
