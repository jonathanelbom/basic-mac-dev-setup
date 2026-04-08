# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Two bash scripts for onboarding uxd designers onto a new Mac with Claude Code. Distributed as a ZIP download — not cloned via git.

## Scripts

- **`1-install`** — installs Homebrew (to `~/.zprofile`), Node, Yarn, GitHub CLI, Claude desktop app, Claude Code, and optionally VS Code + extensions
- **`2-claude`** — takes an API key as an argument, writes `ANTHROPIC_BASE_URL`, `ANTHROPIC_AUTH_TOKEN`, and `CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS` to `~/.zshrc`; deduplicates on re-run

The API key comes from an internal LiteLLM proxy (`https://internal-tool-llm.factset.io/`), not directly from Anthropic.

## Key behaviors to know

- Script 2 has deduplication logic: if `ANTHROPIC_BASE_URL` already exists in `.zshrc`, it strips the old block before re-writing. Re-running it is safe.
- Env vars are written to `~/.zshrc` but take effect only after `source ~/.zshrc` or opening a new terminal — this is a common support issue.
- Script 1 adds Homebrew to `~/.zprofile` (login shells), not `~/.zshrc`. Both files may need to be checked when troubleshooting PATH issues.
- If `claude` is not found after install, the fix is adding `/opt/homebrew/bin/claude` to PATH in `~/.zshrc`.
