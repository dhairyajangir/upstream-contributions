# Accepted upstream contributions

I am Dhairya Jangir ([@dhairyajangir](https://github.com/dhairyajangir)). This index explains eighteen accepted bug fixes across Python, JavaScript, TypeScript, C++, Go and Zsh. The latest additions were verified against their upstream merges on 11 November 2026.

Each entry links a merged PR and a short case study of the problem, implementation and validation. The sixteen case studies cover eighteen PRs because the three Python algorithm fixes share one article.

| Project | Accepted change | Merged (UTC) | Case study |
| --- | --- | --- | --- |
| TheAlgorithms/Python | [Stop bidirectional A* when either frontier is empty](https://github.com/TheAlgorithms/Python/pull/15484) | 2026-10-03 | [Read](case-studies/algorithm-correctness.md) |
| TheAlgorithms/Python | [Fix maximum Fenwick tree range values after updates](https://github.com/TheAlgorithms/Python/pull/15485) | 2026-10-03 | [Read](case-studies/algorithm-correctness.md) |
| TheAlgorithms/Python | [Fix consumed character tracking in Jaro-Winkler matching](https://github.com/TheAlgorithms/Python/pull/15483) | 2026-10-03 | [Read](case-studies/algorithm-correctness.md) |
| mrdoob/three.js | [ColorConverter: Fix HSV conversion at black and white boundaries.](https://github.com/mrdoob/three.js/pull/34806) | 2026-10-05 | [Read](case-studies/three-color-boundaries.md) |
| mrdoob/three.js | [PCDLoader: Respect COUNT when locating ASCII fields.](https://github.com/mrdoob/three.js/pull/34809) | 2026-10-05 | [Read](case-studies/three-pcd-field-offsets.md) |
| mrdoob/three.js | [Octree: Preserve configured subdivision limits.](https://github.com/mrdoob/three.js/pull/34814) | 2026-10-06 | [Read](case-studies/three-octree-options.md) |
| fatedier/frp | [fix: rotate daily counters by calendar date across DST](https://github.com/fatedier/frp/pull/5555) | 2026-10-09 | [Read](case-studies/frp-calendar-counters.md) |
| ohmyzsh/ohmyzsh | [fix(extract): preserve bzip2 archives and honor extraction destination](https://github.com/ohmyzsh/ohmyzsh/pull/14152) | 2026-10-09 | [Read](case-studies/ohmyzsh-bzip2-extraction.md) |
| fatedier/frp | [fix(vhost): preserve buffered HTTP CONNECT tunnel data](https://github.com/fatedier/frp/pull/5556) | 2026-10-09 | [Read](case-studies/frp-buffered-connect.md) |
| thedotmack/claude-mem | [Match zero directories in intermediate globstars](https://github.com/thedotmack/claude-mem/pull/4876) | 2026-10-19 | [Read](case-studies/claude-mem-zero-directory-globstars.md) |
| microsoft/vscode | [Fix UTF-8 encoding of MCP resource URI template values](https://github.com/microsoft/vscode/pull/339846) | 2026-10-22 | [Read](case-studies/vscode-unicode-uri-templates.md) |
| HSF/phoenix | [Restore cell color when disabling selection](https://github.com/HSF/phoenix/pull/1045) | 2026-10-25 | [Read](case-studies/phoenix-selection-cell-color.md) |
| HSF/phoenix | [Release label resources on removal, replacement and event clear](https://github.com/HSF/phoenix/pull/1051) | 2026-11-01 | [Read](case-studies/phoenix-label-resource-lifecycle.md) |
| mrdoob/three.js | [Handle missing normals when computing morphed attributes](https://github.com/mrdoob/three.js/pull/35423) | 2026-11-10 | [Read](case-studies/three-morphed-attributes-missing-normals.md) |
| mavlink/MAVSDK | [Accept generated return-to-launch parameters on ArduPilot](https://github.com/mavlink/MAVSDK/pull/3213) | 2026-11-10 | [Read](case-studies/mavsdk-ardupilot-rtl.md) |
| mavlink/MAVSDK | [Defer a mode-list refresh until the active request completes](https://github.com/mavlink/MAVSDK/pull/3214) | 2026-11-10 | [Read](case-studies/mavsdk-mode-refresh.md) |
| HSF/phoenix | [Skip saved labels without a target in the current event](https://github.com/HSF/phoenix/pull/1063) | 2026-11-11 | [Read](case-studies/phoenix-missing-label-target.md) |
| HEPData/hepdata-converter | [Preserve rows with missing values in CSV exports](https://github.com/HEPData/hepdata-converter/pull/72) | 2026-11-11 | [Read](case-studies/hepdata-ragged-csv.md) |

## What is counted

The eighteen entries above are upstream merges from the campaign beginning 2 October 2026. Open PRs, drafts, closed-unmerged PRs, personal repositories and earlier historical merges are outside this index’s count. Creating or maintaining this portfolio repository adds zero upstream merge credit.

Accepted contributions do not imply employment, project membership or endorsement. Individual PR acceptance does not establish approval of other contributions.

The maintainer-created squash commits for MAVSDK #3213, MAVSDK #3214 and Phoenix #1063 record a different author email from the preferred contribution email. HEPData #72’s contributor commit uses GitHub’s noreply email rather than the preferred address. The PRs are attributed to the GitHub account above; the upstream commit metadata is preserved.

## Review collaboration

On [MarkItDown #2178](https://github.com/microsoft/markitdown/pull/2178), I [suggested a regression test](https://github.com/microsoft/markitdown/pull/2178#issuecomment-6761134119) for transcript-list failures dropping video metadata. The PR author added eight mocked cases and [acknowledged the suggestion](https://github.com/microsoft/markitdown/pull/2178#issuecomment-6767838751). As of 10 November 2026, the PR remains open and is another contributor's work; it is not included in the merge count above.

## Issue reporting

I reported [Dify #43782](https://github.com/langgenius/dify/issues/43782), where a repository component-test reproduction showed JSON example imports could skip the existing depth limit for objects inside arrays. [Redestiny’s #44295](https://github.com/langgenius/dify/pull/44295) addressed the issue and merged on 21 October 2026; the issue report and that other contributor’s fix are not included in the merge count above.

## Campaign checkpoint

[11 November 2026 later checkpoint](status/2026-11-11-hepdata.md) · [Earlier 11 November checkpoint](status/2026-11-11.md) · [10 November checkpoint](status/2026-11-10.md)

## Verification

[evidence.json](evidence.json) records the public merge timestamps, actual merge SHAs, files, merger identities and formal approvals when present. Case studies distinguish tests retained in the final merge from validation supplied during review.

AI assistance was used for implementation, testing, review and these write-ups. Upstream review and merge decisions are attributed to their actual maintainers.
