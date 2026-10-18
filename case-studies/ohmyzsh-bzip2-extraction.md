# Preserve bzip2 archives while respecting the extraction directory

## Problem

The extract plugin's `.bz2` branch decompressed in place, unlike branches that write extracted content into the selected destination. This could remove the archive and put the output beside the original rather than in the requested directory.

## Change

The available bzip2 tool writes decompressed bytes to standard output, which is redirected to the output filename in the extraction directory. The source archive is preserved by default; the existing `-r` option still removes it after successful decompression. Both the `pbzip2` path and the `bunzip2` fallback follow this approach.

## Review and validation scope

The final merged diff changes the extract plugin's production branch and contains no test file. robbyrussell approved and merged the PR after the contributor's ownership confirmation. This case study does not claim that a new upstream test suite landed.

## Upstream evidence

- [ohmyzsh/ohmyzsh #14152](https://github.com/ohmyzsh/ohmyzsh/pull/14152) — merged 2026-10-09T14:01:27Z by [robbyrussell](https://github.com/robbyrussell); [actual merge commit `d7aca552`](https://github.com/ohmyzsh/ohmyzsh/commit/d7aca552b3f04e493c29117870f46cf9bd35957d).
  - [Final `plugins/extract/extract.plugin.zsh`](https://github.com/ohmyzsh/ohmyzsh/blob/d7aca552b3f04e493c29117870f46cf9bd35957d/plugins/extract/extract.plugin.zsh)
