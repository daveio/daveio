# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a GitHub profile repository (daveio/daveio) - a configuration-focused meta-repository that serves as Dave Williams' portfolio hub. It contains no application code; instead, it manages:

- Profile documentation (README.md becomes the GitHub profile page)
- CI/CD automation workflows
- Code quality and security scanning configuration

## Linting Commands

This repository uses **Trunk.io** for linting orchestration:

```sh
trunk check          # Run all enabled linters
trunk check --all    # Check all files (not just changed)
trunk fmt            # Format files with Prettier
trunk upgrade        # Update Trunk and linter versions
```

Pre-commit hooks automatically format files; pre-push hooks run full checks.

## Enabled Linters

| Tool           | Purpose                                        |
| -------------- | ---------------------------------------------- |
| actionlint     | GitHub Actions workflow validation             |
| checkov        | Infrastructure-as-code security scanning       |
| markdownlint   | Markdown linting (Prettier-friendly config)    |
| prettier       | Code formatting (YAML, Markdown)               |
| trufflehog     | Secret/credential detection                    |
| yamllint       | YAML validation                                |
| git-diff-check | Validates git diffs (whitespace, binary files) |

## CI/CD Workflows

Three GitHub Actions workflows are configured:

1. **claude.yaml** - Responds to `@claude` mentions in issues/PRs using Claude Opus
2. **claude-code-review.yaml** - Automated PR reviews on open/sync events
3. **devskim.yaml** - Microsoft DevSkim security analysis on all pushes/PRs

## Merge Requirements

PRs must pass these status checks: CodeQL, DevSkim, Codacy.

## Configuration Locations

- `.trunk/trunk.yaml` - Main Trunk configuration
- `.trunk/configs/` - Linter-specific configs (.yamllint.yaml, .markdownlint.yaml)
- `.github/workflows/` - CI/CD pipelines
- `.github/dependabot.yml` - Automated dependency updates (GitHub Actions)
- `.gemini/config.yaml` - Google Gemini Code Assist settings
