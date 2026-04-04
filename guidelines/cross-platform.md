---
name: Cross-Platform (Windows, macOS, Linux)
description: All examples, paths, and commands must work on Windows, macOS, and Linux without modification
type: guideline
---

# Guideline: Cross-Platform

**Rule:** All examples, paths, and commands in `chevp-workflow` artifacts must work on Windows, macOS, and Linux without modification.

**Why:** The workspace lives on developer machines running different operating systems. Workspace plans, impact maps, and orchestration scripts must be portable so that every contributor can execute them the same way.

**How to apply:** Use forward slashes everywhere in docs and plans. Never hardcode drive letters. Prefer POSIX shell (Git Bash on Windows, bash/zsh on macOS/Linux). For scripts, use Python 3.10+ stdlib rather than shell-specific tools. Standardise line endings via `.gitattributes` (`* text=auto eol=lf`).

## Path conventions

- **Use forward slashes** in all documentation, plans, and stubs: `context/plans/2026-04-04-example.md`.
- **Do not hardcode drive letters** (`C:\`) in workspace plans. Write paths relative to the workspace root (`misc/chevp-workflow/...`) or the repo root.
- When absolute paths are unavoidable in examples, provide both forms:
  - Windows: `C:/chevp/misc/chevp-workflow`
  - macOS/Linux: `~/chevp/misc/chevp-workflow`

## Shell conventions

Prefer shell-agnostic primitives. If a command is shell-specific, show both:

| Task | Windows (PowerShell / Git Bash) | macOS / Linux (bash/zsh) |
|:-----|:---------------------------------|:--------------------------|
| List files | `ls` (Git Bash) / `dir` (cmd) | `ls` |
| Env var | `$env:FOO` / `%FOO%` | `$FOO` |
| Path separator in lists | `;` | `:` |
| Null device | `NUL` (cmd) / `/dev/null` (Git Bash) | `/dev/null` |
| Line endings | CRLF default | LF default |

**Recommendation:** adopt Git Bash on Windows so workspace commands mirror macOS/Linux. All examples in this framework assume POSIX-style shell (Git Bash on Windows, bash/zsh on macOS/Linux).

## Git conventions

- Set `core.autocrlf=input` on macOS/Linux and `core.autocrlf=true` on Windows, OR standardise with `.gitattributes` (`* text=auto eol=lf`).
- Workspace plans never check in platform-specific line endings.

## Scripts (if any are added later)

- Prefer **Python 3.10+** (stdlib only) over shell scripts. Python runs identically on all three platforms.
- If a shell script is required, provide both a `.sh` (POSIX) and a `.ps1` (PowerShell) variant with identical behaviour.
- Never require Windows-only (`cmd`, `.bat`) or Unix-only tools in canonical workflows.

## Commit messages

- Use LF line endings in commit message bodies.
- Avoid non-ASCII characters in `Refs:` trailers to keep them portable across terminals.

## What to test before merging

- Workspace plan opens and renders correctly on both Windows and macOS.
- Paths in the plan resolve under both OSes.
- Any snippet pasted into a terminal works in Git Bash (Windows) and zsh/bash (macOS/Linux).
