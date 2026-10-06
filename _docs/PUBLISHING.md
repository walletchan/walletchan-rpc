# npm releases

Repository extraction does not publish a new npm version. For later releases,
review changes since the last published version and update `CHANGELOG.md`,
`package.json`, and `pnpm-lock.yaml` together. Use semantic versioning.

When MCP needs new RPC behavior, publish RPC before updating and publishing MCP.

From this repository root:

```sh
pnpm install --frozen-lockfile
pnpm build
pnpm test
pnpm pack:dry-run
pnpm publish:dry-run
# After reviewing the packed contents and completing wallet transport QA:
pnpm publish:npm
```

Verify the published version with `npm view @walletchan/rpc version`.
Transport signing changes require wallet approval QA for all supported signer
paths, including a real Ledger device when hardware signing is affected.
