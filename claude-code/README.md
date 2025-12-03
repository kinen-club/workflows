# Kinen Claude Code Plugin

Structured iterative refinement methodology for Claude Code.

## Installation

```bash
# Add to your Claude Code plugins
claude plugins add kinen-club/agents/claude-code
```

Or manually copy to your Claude Code plugins directory.

## Commands

| Command | Description |
|---------|-------------|
| `/session` | Start a new kinen session |
| `/round` | Create the next round in current session |
| `/summarize` | Summarize and close the session |

## Skills

- **kinen-core** - Core methodology for round-based exploration

## Agents

- **kinen-facilitator** - Deep thinking partner (uses Opus model)

## Usage

```
User: /session
Claude: "I'm using the kinen methodology. What are we exploring today?
        - 🏗️ Architecture
        - 🔧 Implementation
        - ✍️ Creative Writing
        - 📚 Non-Fiction
        - 🔬 Research"

User: "Design a new caching layer for our API"
Claude: [Creates session folder, init.md, technical-spec.md]
Claude: [Begins Round 01: Foundation with probing questions]

... rounds of exploration ...

User: /summarize
Claude: [Creates session-summary.md with all decisions]
```

## Session Structure

```
sessions/
  20251202-01-caching-layer/
    init.md                    # Session goals
    rounds/
      01-foundation.md         # Initial exploration
      02-cache-strategy.md     # Deep dive
      03-invalidation.md       # Specific topic
    artifacts/
      technical-spec.md        # Living document
    session-summary.md         # Final summary
```

## Learn More

- [Kinen Methodology](../methodology/core.md)
- [kinen.club](https://kinen.club)

