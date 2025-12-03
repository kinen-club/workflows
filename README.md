# Kinen Agents

AI agent integrations for the kinen methodology.

## Overview

This repo contains integrations for different AI agent platforms, all using the same [kinen methodology](methodology/core.md).

| Platform | Location | Description |
|----------|----------|-------------|
| **GitHub Actions** | `.github/workflows/` | Email-triggered Aider sessions |
| **Claude Code** | `claude-code/` | Plugin with commands and skills |
| **Cursor** | `cursor/` | Rules file integration |

## Methodology

The kinen methodology lives in [`methodology/core.md`](methodology/core.md).

All agent integrations reference this single source of truth.

---

## GitHub Actions (Email-based)

Reusable workflows for email-triggered AI sessions using Aider.

### Usage in your space

```yaml
# .github/workflows/kinen.yml
name: Kinen
on:
  repository_dispatch:
    types: [email_session_start, email_session_continue]
  issue_comment:
    types: [created]

jobs:
  agent:
    uses: kinen-club/agents/.github/workflows/agent.yml@main
    secrets: inherit
```

### Available Workflows

| Workflow | Description |
|----------|-------------|
| `agent.yml` | Main AI session handler |
| `onboard.yml` | Welcome workflow for new spaces |

---

## Claude Code Plugin

Native Claude Code integration with commands and skills.

### Installation

```bash
claude plugins add kinen-club/agents/claude-code
```

### Commands

| Command | Description |
|---------|-------------|
| `/session` | Start a new kinen session |
| `/round` | Create next round |
| `/summarize` | Summarize and close session |

See [`claude-code/README.md`](claude-code/README.md) for details.

---

## Cursor Integration

Drop-in rules file for Cursor.

### Setup

Copy to your project:

```bash
curl -o .cursorrules https://raw.githubusercontent.com/kinen-club/agents/main/integrations/.cursorrules
```

See [`cursor/README.md`](cursor/README.md) for details.

---

## Drop-in Files

Ready-to-use integration files in [`integrations/`](integrations/):

| File | Use For |
|------|---------|
| `CLAUDE.md` | Claude Code workspaces |
| `.cursorrules` | Cursor projects |

---

## Learn More

- [kinen.club](https://kinen.club) - Email-based kinen service
- [kinen-club/space](https://github.com/kinen-club/space) - Template repo
- [Methodology](methodology/core.md) - Full kinen methodology

## License

MIT
