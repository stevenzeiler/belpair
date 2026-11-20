# Status

Updated 2026-11-20.

## What works
- Unknown. The code was not built or run during the docs pass.

## What's broken or unknown
- `npm test` references a `test/` folder that is not in the repo.
- The README import name was `ecpair` upstream; check the published package matches the `belpair` name.
- `src/` is git-ignored but `main` points at it, so consumers need the build output from npm.
- Whether `belpair` is published on npm and used by a live app is unknown, ask Steven.
- The previous README held an upstream example WIF string. It was replaced with a placeholder here; it is a public documentation example, but git history still contains it.

## What's next
- Decide if this stays as a fork or gets archived (Steven's call).
- If kept: restore tests, build once, run `npm audit`.

## Not yet from the standard
- CONTRIBUTING.md (a pointer to upstream exists), SECURITY.md
- LICENSE: present (MIT)
- .editorconfig
- .github issue and PR templates
- Dependabot config
- ci.yml with gitleaks
- CloudEvents catalog
- Product ONE-PAGER
- Default branch is already `main`
