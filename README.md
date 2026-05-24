# Golain documentation

End-user documentation for the Golain IoT platform, built with [Mintlify](https://mintlify.com).

**Repository:** [golain-io/docs](https://github.com/golain-io/docs)

## Scope

| Tab | Covers |
|-----|--------|
| **Platform** | Getting started, web console (`pw`) |
| **Tools** | `platform-tui` CLI/TUI, `golain-cli` |
| **Edge** | Omega runtime, JITR, deployment, SQLite sync |
| **Self-hosted** | vm-edge operator stack, local dev |

Product repositories:

- [ilyama](https://github.com/golain-io/ilyama) — API, workers, MQTT broker
- [pw](https://github.com/golain-io/pw) — web console
- [omega](https://github.com/golain-io/omega) — edge client

## Local preview

```bash
npm i -g mint
mint dev
```

Open `http://localhost:3000`.

```bash
mint broken-links
```

## Publishing

Connect the Mintlify GitHub app in the [dashboard](https://dashboard.mintlify.com) to deploy on push to `main`.

## AI-assisted editing

```bash
npx skills add https://mintlify.com/docs
```

For agent instructions see [AGENTS.md](./AGENTS.md).

Mintlify **admin MCP** (write access) is configured in Cursor via `mintlify-admin` in `~/.cursor/mcp.json`. Credentials are stored locally in `~/secured/mintlify-mcp.env` — not in this repo.

## Contributing

1. Branch from `main`
2. Edit MDX under the appropriate section
3. Update `docs.json` when adding or renaming pages
4. Run `mint broken-links` before opening a PR

See [CONTRIBUTING.md](./CONTRIBUTING.md) for Mintlify starter-kit conventions.
