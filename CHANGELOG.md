# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-04-25

### Added
- `SKILL.md` — structured 7-section session handoff skill for Claude Code
- Trigger phrases: `session handoff`, `wrap up session`, `hand off`, `handoff summary`
- Fixed output template: Where it started, Decisions locked, Key files, Running state, Verification, Deferred + open questions, Pick up here
- Chat-only output by design (never writes to file)
- README with install instructions (macOS/Linux/Windows), usage guide, and full example output
- MIT license, SECURITY.md, CITATION.cff
- Community health files: CONTRIBUTING.md, CODE_OF_CONDUCT.md (Contributor Covenant v2.1), SUPPORT.md
- Issue templates: bug report, feature request (YAML forms)
- CI workflow: Markdown lint on push and pull request

[Unreleased]: https://github.com/thenguyenvn90/claude-session-handoff/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/thenguyenvn90/claude-session-handoff/releases/tag/v1.0.0
