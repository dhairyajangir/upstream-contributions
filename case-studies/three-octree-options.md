# Honor Octree subdivision options throughout the tree

## Problem

An Octree's root accepted `maxLevel` and `trianglesPerLeaf`, but freshly constructed children retained their default values. Recursive splitting could therefore ignore the caller's subdivision limits.

## Change

Each new child inherits both options from its parent. The existing splitting and intersection algorithms remain in place.

## Validation in the merged change

The accepted addon tests construct a real sphere mesh, check depth with a restricted maximum level or larger leaf capacity, and confirm the ray intersection distance remains three units. Both regressions and their addon registration landed with the source change. Mugen87 approved and merged the PR.

## Upstream evidence

- [mrdoob/three.js #34814](https://github.com/mrdoob/three.js/pull/34814) — merged 2026-10-06T09:52:05Z by [Mugen87](https://github.com/Mugen87); [actual merge commit `00887e72`](https://github.com/mrdoob/three.js/commit/00887e72c0d39a90bb5ce66eb6935147eb4cd5e4).
  - [Final `examples/jsm/math/Octree.js`](https://github.com/mrdoob/three.js/blob/00887e72c0d39a90bb5ce66eb6935147eb4cd5e4/examples/jsm/math/Octree.js)
  - [Final `test/unit/addons/math/Octree.tests.js`](https://github.com/mrdoob/three.js/blob/00887e72c0d39a90bb5ce66eb6935147eb4cd5e4/test/unit/addons/math/Octree.tests.js)
  - [Final `test/unit/three.addons.unit.js`](https://github.com/mrdoob/three.js/blob/00887e72c0d39a90bb5ce66eb6935147eb4cd5e4/test/unit/three.addons.unit.js)
