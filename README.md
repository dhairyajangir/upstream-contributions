# Accepted upstream contributions

I am Dhairya Jangir ([@dhairyajangir](https://github.com/dhairyajangir)). This index explains thirteen accepted bug fixes across Python, JavaScript, TypeScript, Go and Zsh. The latest addition was verified against its upstream merge on 10 November 2026.

Each entry links a merged PR and a short case study of the problem, implementation and validation. The eleven case studies cover thirteen PRs because the three Python algorithm fixes share one article.

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

## What is counted

The thirteen entries above are upstream merges from the campaign beginning 2 October 2026. Open PRs, drafts, closed-unmerged PRs, personal repositories and earlier historical merges are outside this index’s count. Creating or maintaining this portfolio repository adds zero upstream merge credit.

Accepted contributions do not imply employment, project membership or endorsement. Individual PR acceptance does not establish approval of other contributions.

## Verification

[evidence.json](evidence.json) records the public merge timestamps, actual merge SHAs, files, merger identities and formal approvals when present. Case studies distinguish tests retained in the final merge from validation supplied during review.

AI assistance was used for implementation, testing, review and these write-ups. Upstream review and merge decisions are attributed to their actual maintainers.
