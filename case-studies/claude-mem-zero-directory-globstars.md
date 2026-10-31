# Make intermediate globstars match zero directories

## Problem

An intermediate `**/` segment required at least one directory. For example, `/workspace/**/private` matched `/workspace/team/private` but missed `/workspace/private` itself. That gap affected project exclusions and named project environments that share the matcher.

## Change

The matcher recognizes a complete globstar directory segment before processing the other wildcard tokens. Its directory and slash become optional together, allowing zero or more directories while preserving ordinary `*` behavior. The configuration documentation explains the direct-child case and the separate trailing `/**` rule for descendants.

## Validation in the merged change

The final merge retains the source fix, documentation and both test files. Regressions cover direct and nested matches, leading and consecutive globstars, Windows and home-directory normalization, the shared deny-list matcher, and named environments. The production source and both test blobs match the submitted versions; the documentation's added explanation is retained in the merge's updated surrounding context.

Both upstream CI and Windows workflows completed successfully, with eight successful check records. Earlier local full-suite failures remain documented. The owner, thedotmack, confirmed successful CI on the submitted commit, marked it ready and merged it; the owner attributed the earlier local failures to environment and timeout noise. There was no separate formal APPROVED review.

## Upstream evidence

- [thedotmack/claude-mem #4876](https://github.com/thedotmack/claude-mem/pull/4876) — merged 2026-10-19T06:42:10Z by [thedotmack](https://github.com/thedotmack); [actual merge commit `c9b79ecd`](https://github.com/thedotmack/claude-mem/commit/c9b79ecdaa7fe1950cb921603c65b57f6a41eebe).
  - [Final `src/utils/project-filter.ts`](https://github.com/thedotmack/claude-mem/blob/c9b79ecdaa7fe1950cb921603c65b57f6a41eebe/src/utils/project-filter.ts)
  - [Final `tests/utils/project-filter.test.ts`](https://github.com/thedotmack/claude-mem/blob/c9b79ecdaa7fe1950cb921603c65b57f6a41eebe/tests/utils/project-filter.test.ts)
  - [Final `tests/utils/project-environments.test.ts`](https://github.com/thedotmack/claude-mem/blob/c9b79ecdaa7fe1950cb921603c65b57f6a41eebe/tests/utils/project-environments.test.ts)
  - [Final `docs/public/configuration.mdx`](https://github.com/thedotmack/claude-mem/blob/c9b79ecdaa7fe1950cb921603c65b57f6a41eebe/docs/public/configuration.mdx)
  - [Owner's acceptance and validation explanation](https://github.com/thedotmack/claude-mem/pull/4876#issuecomment-6261339282)
