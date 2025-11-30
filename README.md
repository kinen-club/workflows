# Kinen Reusable Workflows

Centralized GitHub Actions workflows for the Kinen platform.

## What's Here

This repository contains reusable workflows that are called by Kinen user repositories.

### Workflows

- **`onboard.yml`** - Handles user onboarding when they first push to their Kinen workspace
- **`agent.yml`** - Processes email-triggered sessions using Aider AI

## Usage

User repositories call these workflows via minimal caller files:

```yaml
# In user's repo: .github/workflows/onboard-caller.yml
name: Kinen Onboarding

on:
  push:
    branches: [main]

jobs:
  onboard:
    uses: kinen-club/workflows/.github/workflows/onboard.yml@main
    secrets: inherit
```

```yaml
# In user's repo: .github/workflows/agent-caller.yml
name: Kinen Agent

on:
  repository_dispatch:
    types: [email_session_start, email_session_continue]

jobs:
  session:
    uses: kinen-club/workflows/.github/workflows/agent.yml@main
    secrets:
      OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
```

## Benefits

✅ Users get workflow updates automatically
✅ Minimal code in user repositories
✅ Centralized maintenance and bug fixes
✅ Version pinning available (`@main`, `@v1`, etc.)

## Architecture

```
Email arrives → Bird.com → Club Platform → repository_dispatch
                                              ↓
                                         agent.yml (this repo)
                                              ↓
                                         Creates issue
                                         Runs Aider
                                         Commits code
                                         Sends email
```

## Configuration

### Required Secrets (in user repos)

- `OPENAI_API_KEY` - For Aider AI code generation

### Optional Inputs

Both workflows accept a `relay_url` input to customize the relay endpoint:

```yaml
jobs:
  session:
    uses: kinen-club/workflows/.github/workflows/agent.yml@main
    with:
      relay_url: 'https://custom-relay.example.com'
    secrets:
      OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
```

## Development

To test changes:

1. Create a test branch: `git checkout -b test-feature`
2. Update workflows
3. Point a test repo to your branch:
   ```yaml
   uses: kinen-club/workflows/.github/workflows/agent.yml@test-feature
   ```
4. Test thoroughly
5. Merge to main when ready

## Versioning

We use semantic versioning with Git tags:

- `@main` - Latest version (may have breaking changes)
- `@v1` - Major version 1 (stable, no breaking changes)
- `@v1.2` - Specific minor version
- `@v1.2.3` - Specific patch version

**Recommendation for users:** Pin to `@v1` for stability.

## Related Repositories

- **[kinen-club/space](https://github.com/kinen-club/space)** - Template repository for users
- **[kinen-club/relay](https://github.com/kinen-club/relay)** - Cloudflare Worker for email routing

## License

MIT
