# Install — OntoRamp Decision Intelligence (for AI agents)

You are an AI agent (e.g. Cline) setting up the **OntoRamp Decision Intelligence** MCP server. It is a **hosted, remote** server (Streamable HTTP). There is **nothing to clone, build, install, or run locally** — add one config entry pointing at the hosted endpoint with the user's API key.

## Step 1 — Ensure the user has a free API key

Ask the user for their OntoRamp API key (`or_free_…`). If they don't have one, tell them to get a free key — no credit card — at **https://ontoramp.com/mcp** (emailed). Do **not** invent a key.

## Step 2 — Add the server to the MCP config

In Cline that is `~/.cline/mcp.json` (CLI) or the Cline UI → MCP Servers → Configure. Merge into any existing `mcpServers`:

```json
{
  "mcpServers": {
    "ontoramp-decision-intelligence": {
      "url": "https://ontoramp-decision-intelligence.fly.dev/mcp",
      "headers": { "Authorization": "Bearer <USER_API_KEY>" },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Replace `<USER_API_KEY>` with the user's key. Transport is **Streamable HTTP**; do not set `command`/`args` (not a stdio server).

## Step 3 — Confirm reachability

```bash
curl https://ontoramp-decision-intelligence.fly.dev/health
```

Expect `{"status":"ok",...}`.

## Step 4 — Available tools

- `find_decision_precedent` — look up prior relevant decisions (Free tier, read-only)
- `log_decision` — record a decision with authority context (Developer tier, **write — auth required**)
- `evaluate_decision` — check a decision for authority gaps / precedent conflicts (Developer tier)
- `request_assessment` — request an Agentic Readiness Assessment (all tiers)

On the **free tier** only `find_decision_precedent` (read) and `request_assessment` work; the write/evaluate tools return an upgrade message — that is expected, not an error. `log_decision` never accepts unauthenticated writes by design.

## Notes

- No environment variables, dependencies, or local process.
- Bearer API key in the `Authorization` header (or `?api_key=` query param if headers are unavailable).
