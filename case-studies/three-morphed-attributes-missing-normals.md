# Handle missing normals in morphed geometry

## Problem

`computeMorphedAttributes()` reads both position and normal data from a geometry. A mesh, line or points geometry can have positions without normals; in that case, accessing the missing normal attribute caused the computation to throw instead of returning morphed positions.

## Change

The accepted change skips normal processing when the geometry has no normal attribute. It still computes the position result and returns `undefined` for both normal fields. Normal processing remains in place when the attribute exists. The existing partial draw-range limitation is unchanged.

## Review and validation scope

The original submission included three new tests covering position-only meshes, lines, points, material groups and a skinned mesh. On the original submitted version, local validation included `npm test` and independent API probes. During review, the implementation was revised and the proposed tests were removed. The final merged diff changes the utility source only; those proposed tests did not land. The merge credits Michael Herzog as a co-author. AI assisted with implementation, tests and review.

## Upstream evidence

- [mrdoob/three.js #35423](https://github.com/mrdoob/three.js/pull/35423) — merged 2026-11-10T09:15:53Z by [Mugen87](https://github.com/Mugen87); [actual merge commit `c4801720`](https://github.com/mrdoob/three.js/commit/c480172072a627207cff03c73bda79c67c97114d).
  - [Final `examples/jsm/utils/BufferGeometryUtils.js`](https://github.com/mrdoob/three.js/blob/c480172072a627207cff03c73bda79c67c97114d/examples/jsm/utils/BufferGeometryUtils.js)
