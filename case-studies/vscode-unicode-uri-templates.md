# Encode Unicode resource URI template values correctly

## Problem

VS Code's URI template expansion encoded each UTF-16 code unit as though it were a byte. An accented value such as `café` therefore produced `caf%E9` instead of UTF-8 `caf%C3%A9`. Chinese text and emoji also expanded incorrectly. Prefix limits used UTF-16 substring positions and could split an emoji's surrogate pair.

This affects the URI template values used for MCP resources, including names that contain non-ASCII text.

## Change

The encoder uses UTF-8 percent encoding and explicitly escapes the additional punctuation that simple expansion must encode. Prefix limits count Unicode code points with `Array.from`, preserving complete supplementary characters.

## Validation in the merged change

The source and regression test file both landed. Tests cover accented and Chinese values, emoji, punctuation, and prefixes containing supplementary characters. The earlier local validation recorded 29 targeted repository-runner tests and changed-file ESLint passing; no live MCP/Electron integration result was claimed.

Three reviewers—connor4312, roblourens and anthonykim1—approved the PR, and connor4312 merged it. Six upstream workflow runs completed successfully.

## Upstream evidence

- [microsoft/vscode #339846](https://github.com/microsoft/vscode/pull/339846) — merged 2026-10-22T01:59:58Z by [connor4312](https://github.com/connor4312); [actual merge commit `070abe7c`](https://github.com/microsoft/vscode/commit/070abe7cd0e6434522949ad924c2e008c2300fe3).
  - [Final `src/vs/base/common/uriTemplate.ts`](https://github.com/microsoft/vscode/blob/070abe7cd0e6434522949ad924c2e008c2300fe3/src/vs/base/common/uriTemplate.ts)
  - [Final `src/vs/base/test/common/uriTemplate.test.ts`](https://github.com/microsoft/vscode/blob/070abe7cd0e6434522949ad924c2e008c2300fe3/src/vs/base/test/common/uriTemplate.test.ts)
  - [First human approval](https://github.com/microsoft/vscode/pull/339846#pullrequestreview-5606947712)
