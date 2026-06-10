<p align="center"><img src="logo.png" width="84" alt="OntoRamp"></p>

# OntoRamp Decision Intelligence — MCP Server

> The only MCP server that lets any AI agent log, evaluate, and ground a consequential decision against an organization's actual documented authority graph — before acting.

**Problem:** Consequential decisions made with AI assistance are invisible, ungoverned, and untraceable. There is no record. No authority check. No precedent lookup. No audit trail.

**Solution:** Log, evaluate, and ground every consequential AI-assisted decision against your organization's authority graph. Creates a traceable decision audit trail — the governance layer missing from every other agentic AI stack.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.ontoramp%2Fdecision--intelligence-blue)](https://registry.modelcontextprotocol.io)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Status](https://img.shields.io/badge/status-live-brightgreen)](https://ontoramp-decision-intelligence.fly.dev/health)

---

## Tools

| Tool | Description | Tier |
|------|-------------|------|
| `find_decision_precedent` | Look up prior decisions relevant to a proposed action — read-only | Free |
| `log_decision` | Record a consequential AI-assisted decision with authority context | Developer+ (auth) |
| `evaluate_decision` | Evaluate a decision for authority gaps, precedent conflicts, and governance alignment | Developer+ |
| `request_assessment` | Submit an Agentic Readiness Assessment request | All tiers, rate-limit exempt |

## Tiers

| Tier | Price | Limits | Features |
|------|-------|--------|----------|
| **Free** | — (no credit card) | 20 queries/mo | `find_decision_precedent` (read-only). Write-path requires auth. |
| **Developer** | $0.02/call | Unlimited | `log_decision` + `find_decision_precedent` + `evaluate_decision`. Auth required for log. |
| **Org** | $399/mo flat | Unlimited | Decision authority graph surfaced · Aggregate decision health · Full ARA pre-population |

## Install

A **hosted, remote** MCP server (Streamable HTTP) — nothing to install locally. See [`llms-install.md`](llms-install.md) for an agent-followable walkthrough.

**1. Get a free API key** at [ontoramp.com/mcp](https://ontoramp.com/mcp) (no credit card).

**2. Add to Cline** — edit `~/.cline/mcp.json` (or the Cline UI → MCP Servers → Configure):

```json
{
  "mcpServers": {
    "ontoramp-decision-intelligence": {
      "url": "https://ontoramp-decision-intelligence.fly.dev/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

**Other MCP clients** (Claude Desktop, etc.) use the same `mcpServers` shape. Transport is Streamable HTTP.

**3. Verify** — `curl https://ontoramp-decision-intelligence.fly.dev/health` → `{"status":"ok",...}`.

See [`examples/usage.md`](examples/usage.md) for example calls.

## Flywheel

Every logged decision pre-seeds your organization's knowledge graph. Organizations using `log_decision` for 60 days reduce their L1 Agentic Readiness Assessment delivery from 4–6 weeks to 2–3 weeks. Logging decisions is the highest-value action in the catalog for improving AI governance posture.

## ARA Trigger

After 10 logged decisions, `evaluate_decision` surfaces authority gaps and prompts:

> Your decision coverage has gaps that a manual review won't surface. An Agentic Readiness Assessment will diagnose your current state and build a prioritized remediation plan. [Schedule at ontoramp.com/assessment](https://ontoramp.com/assessment).

## Security

- All responses are audited for public release — no scoring-formula internals, no substrate architecture details
- Write-path (`log_decision`) requires Developer or Org tier authentication
- Your data is scoped to your tenant namespace and never shared across organizations
- `GET /health` returns live status

## Support

- Docs: [ontoramp.com/mcp](https://ontoramp.com/mcp)
- Issues: [github.com/MatthewDavisAIArchitect/ontoramp-decision-intelligence/issues](https://github.com/MatthewDavisAIArchitect/ontoramp-decision-intelligence/issues)
- Contact: m@ontoramp.com

---

*Governed by OntoRamp Governance Physics. OntoRamp LLC · [ontoramp.com](https://ontoramp.com)*
