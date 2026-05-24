# Golain documentation — agent instructions

End-user-facing Mintlify site for Golain (ilyama backend, pw web console, omega edge client). Source: [golain-io/docs](https://github.com/golain-io/docs).

## Repository layout

```
docs.json              # Mintlify navigation and theme
index.mdx              # Home
getting-started/       # Quickstart, concepts, paths
console/               # Web UI (pw) guides
tools/                 # platform-tui + golain-cli
edge/                  # Omega runtime + data sync
self-hosted/           # vm-edge and local dev
```

Developer/contributor docs stay in each product repo (`ilyama/docs/knowledge`, `omega/docs/developer-*`, `pw/docs/*`). Do not duplicate internal architecture here unless rewritten for operators.

## Terminology

| Term | Usage |
|------|--------|
| **Console** | Web UI (`pw`) — not "dashboard" alone |
| **platform-tui** | Official CLI/TUI from ilyama — not "platform CLI" interchangeably in commands |
| **Omega** | Edge runtime product name |
| **Organization / Project / Fleet / Device** | Capitalized when referring to platform resources |
| **JITR** | Just-in-Time Registration — spell out once per page |

## Style

- Second person, active voice ("Create a fleet", not "A fleet is created")
- Sentence case headings
- Bold for UI labels: Click **Create fleet**
- Code formatting for commands, paths, env vars, and API fields
- One idea per sentence; prefer tables and steps for procedures

## Content boundaries

**Include:** setup, walkthroughs, operator troubleshooting, CLI/TUI reference, edge deployment, self-hosted vm-edge.

**Exclude:** sqlc/eventbus worker internals, ReBAC tuple implementation, integration platform v3 substrate details, frontend module scaffolding (`pw/docs/feature-module-guide.md`).

Link to GitHub source docs for protocol specs instead of copying unbounded wire details.

## Mintlify workflow

```bash
npm i -g mint
mint dev          # localhost:3000
mint broken-links
```

After navigation changes, edit `docs.json` and run `mint broken-links`.

Install writing skill: `npx skills add https://mintlify.com/docs`

## Mintlify admin MCP (Cursor)

Write access uses **Mintlify admin MCP** at `https://mcp.mintlify.com`.

Client credentials live in `~/secured/mintlify-mcp.env` (never commit). Cursor invokes `~/secured/mintlify-mcp-proxy.sh`, which exchanges credentials for a bearer token and runs `mcp-remote`.

Typical agent flow:

1. `checkout` branch with slug (for example `add-edge-jitr`)
2. `edit_page` / `write_page` / `update_config`
3. `diff` → `save` with `mode: "pr"`

Reload Cursor MCP after changing `~/.cursor/mcp.json`.

## Source material when updating

| Topic | Canonical source |
|-------|------------------|
| platform-tui | `ilyama/tools/platform-tui/README.md` |
| Omega install/configure | `omega/docs/*.md` |
| vm-edge | `ilyama/infra/deploy/vm-edge/README.md` |
| Console features | `pw/README.md` + product UI |
| golain-cli | `golain-cli/ReadME.md` |
| Edge sync protocol | `ilyama/docs/knowledge/edge-client-guide.md` |

When upstream changes, update the corresponding Mintlify page and cross-links.

## Open items (known gaps)

- Console walkthroughs need screenshots from `pw` and production
- golain-cli install section needs release artifact URLs when published
- API reference tab not yet wired to `ilyama` OpenAPI — add when public API docs are scoped

## Edge SQLite sync docs

Extensive operator + integrator coverage under `edge/data-sync/` (20 pages):

| Section | Pages |
|---------|-------|
| Concepts | overview, how-it-works, lineages-and-staging, schema-governance, registry-coalescing, backpressure |
| Omega | omega-setup, configuration, capture-strategies, provisioning-checklist |
| Operations | schema-review-workflow, platform-tui-guide, api-reference, querying-data, troubleshooting |
| Wire protocol | topics-and-connection, payload-formats, downlink-control, limits-dedup-errors |

Canonical wire spec remains [ilyama edge-client-guide](https://github.com/golain-io/ilyama/blob/main/docs/knowledge/edge-client-guide.md) — Mintlify pages adapt for end users.
