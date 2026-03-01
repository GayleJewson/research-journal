# Medium Comment Responder

**Status:** Planning (awaiting Nick's decisions)
**Started:** 2026-03-01

## Goal

Enable Claudius (and potentially Lyra) to read and reply to comments on Medium articles about AI-human collaboration. Browser automation since Medium has no comment API.

## Architecture

- **Playwright MCP server** (`@playwright/mcp`) added to Claude Code settings
- **medium-loop.sh** — parallel polling loop alongside email loop
- **Headless Chromium** in Docker container
- **Session persistence** — cookies on encrypted Fly.io volume
- **Shared quota** — Medium turns count toward weekly 1200-turn budget

## Key Findings (Research)

- Medium's official API is publishing-only, no comment endpoints, no new API tokens issued
- Microsoft's `@playwright/mcp` (npm) exposes ~25 browser tools via MCP protocol
- Uses accessibility tree (not screenshots) — fast, resilient to CSS changes
- Medium calls comments "responses" — they're mini-stories under the article
- May require paid Medium membership to comment (varies by publication settings)
- Chromium needs ~1GB RAM — may need to bump Fly.io from 512MB

## Decisions Pending (Nick)

1. Medium account — new dedicated account or existing?
2. Auth method — Google OAuth (automatable) vs email magic links (painful)
3. Poll frequency — 6-12 hours suggested
4. Which articles to monitor — start with collaboration article

## Implementation Steps

1. Dockerfile: Node.js 18+ + @playwright/mcp + Chromium
2. settings.json: add Playwright MCP server config
3. medium-loop.sh: polling loop
4. medium-session.sh: login/session management
5. State tracking: JSON file of replied-to comment IDs
6. Persona: Medium-specific voice (shorter, casual, colorful language)
7. Quota: integrate with agent-state.json
8. Graceful degradation: error handling, owner alerts

## Risks

- Medium UI changes could break automation
- 512MB container may be too small for Chromium (need 1GB)
- Session expiry requires manual re-auth
- ToS gray area (mitigated by transparency in account bio)
