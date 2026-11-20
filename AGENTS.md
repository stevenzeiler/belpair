# AGENTS.md

## What this is
`belpair`, a fork of bitcoinjs/ecpair (SECP256k1 key pairs) depending on `belcoinjs-lib`. Mostly upstream code. See README.md.

## Stack
- TypeScript ^4.4, compiled with `tsc` to `src/` (git-ignored).
- Runtime deps: `@noble/hashes`, `belcoinjs-lib`, `wif`, `typeforce`.
- `engines.node` says >=8; the dev tooling (mocha 7, ts-node 8, tslint) is old. Use a modern Node but expect friction. Not verified.

## Layout
- `ts_src/` source (`ecpair.ts`, `index.ts`, `types.ts`).
- `src/` build output, not committed.
- `docs/STATUS.md` current state. Keep it current.

## Commands
- Install: `npm install` (a `bun.lockb` also exists).
- Build: `npm run build`
- Lint: `npm run lint`; format check: `npm run format:ci`
- Tests: `npm test` is defined but the `test/` folder is missing, so it is known not to work as is.

## Rules
- Tests with every change (add a `test/` folder first).
- Never commit secrets: no real WIF keys or private keys in code, tests or docs.
- Conventional Commits.
- Keep `docs/STATUS.md` current.
- Keep the MIT licence and upstream credit.

## What agents may and may not do
- May: fix bugs, improve docs, add tests, open PRs.
- May not: archive the repo, publish to npm, rewrite git history, or change dependencies on key-handling code without Steven.
