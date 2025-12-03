# Kinen Cursor Integration

Use the kinen methodology in Cursor.

## Setup

Copy `.cursorrules` to your project root:

```bash
curl -o .cursorrules https://raw.githubusercontent.com/kinen-club/agents/main/cursor/.cursorrules
```

Or copy from `integrations/.cursorrules` in this repo.

## Usage

The rules file instructs Cursor to use the kinen methodology:
- Round-based iterative exploration
- Session folder structure
- Living document updates
- Decision documentation

### Start a Session

Just tell Cursor what you want to explore:

```
"Let's design a new authentication system using kinen methodology"
```

Cursor will:
1. Create session folder in `sessions/`
2. Start with foundation round
3. Progress through exploration rounds
4. Update living document after each round

### Commands (Natural Language)

- "Start a new kinen session for [topic]"
- "Continue to the next round"
- "Summarize and close this session"

## Session Types

| Type | Living Document | Use For |
|------|-----------------|---------|
| Architecture | `technical-spec.md` | System design, API design |
| Implementation | `implementation-plan.md` | Code specs, refactoring |
| Creative Writing | `outline.md` | Fiction, screenplay |
| Non-Fiction | `outline.md` | Technical writing |

## Learn More

- [Kinen Methodology](../methodology/core.md)
- [kinen.club](https://kinen.club)

