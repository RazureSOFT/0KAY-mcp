# 0KAY-mcp

MCP (Model Context Protocol) client gateway for the 0KAY platform, together
with the shared protobuf service definitions.

This repository ships two directories:

- `mcp/` — the `@0kay/mcp` Node.js package. It provides the MCP client gateway
  used by `0kay-agent`; the package manifest is `mcp/manifest.json`.
- `proto/` — the protobuf contracts shared by Core, MOCR, LIFE, the agent and
  plugins (`agent`, `core`, `life`, `mocr`, `plugin` packages). The `0kay-agent`
  installer consumes this directory to build its gRPC bindings.

The layout mirrors the umbrella `0KAY` repository so that 0kay-pm and the agent
installer can consume this repository without further changes.

## Install

```powershell
0kay-pm install @razuresoft/0kay-mcp@0.1.0
```

`0kay-pm` downloads the `v0.1.0` source archive and runs the commands declared in
`mcp/manifest.json` (`npm ci`, `npm run build`). The package is a library — it
declares no `start` command, so installing it alone starts no process.
`0kay-pm install @razuresoft/0kay-agent` installs it automatically as a
dependency.

## Develop

```powershell
cd mcp
npm ci
npm run build   # tsc → dist/
npm test        # build + node --test dist/regression.test.js
```

Requires Node.js 20+.

## Version

`mcp/manifest.json` holds the release version and must be bumped together with
the git tag when cutting a release.
