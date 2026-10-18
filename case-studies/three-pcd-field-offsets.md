# Read ASCII point-cloud fields at their true offsets

## Problem

A PCD field can contain more than one value, declared with `COUNT`. The ASCII parser used the field's ordinal as its token offset. A multi-value field before coordinates or color shifted later tokens and caused the wrong data to be read.

## Change

ASCII offsets now accumulate the preceding fields' counts. This makes an offset describe the actual token position, consistently with the binary path's existing treatment of field counts.

## Review and validation scope

Mugen87 approved the change as making the ASCII path consistent with the binary one, and merged it. The final accepted diff changes the production parser only. The maintainer removed the proposed test file and registration before merge; those tests are not represented here as landed upstream coverage.

## Upstream evidence

- [mrdoob/three.js #34809](https://github.com/mrdoob/three.js/pull/34809) — merged 2026-10-05T20:50:45Z by [Mugen87](https://github.com/Mugen87); [actual merge commit `28ed5739`](https://github.com/mrdoob/three.js/commit/28ed5739ce6c099f32704e8ddc5a1147c3aa2b1a).
  - [Final `examples/jsm/loaders/PCDLoader.js`](https://github.com/mrdoob/three.js/blob/28ed5739ce6c099f32704e8ddc5a1147c3aa2b1a/examples/jsm/loaders/PCDLoader.js)
