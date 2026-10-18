# Finite HSV conversion at black and white boundaries

## Problem

HSV/HSL conversion divides by expressions that become zero at achromatic boundaries. Setting black or white, or converting black back to HSV, could produce an undefined saturation rather than a finite color.

## Change

The conversion explicitly uses zero saturation at the degenerate black/white lightness boundaries and when the HSV value is zero. Existing nondegenerate formulas and the working color space are retained.

## Validation in the merged change

The accepted addon unit tests cover black, white, gray, primary colors, clamping, hue wrapping, round trips and the linear working color space. The source fix, unit test file and addon registration all landed. Mugen87 approved and merged the PR. These unit checks are not a claim of exhaustive GPU rendering coverage.

## Upstream evidence

- [mrdoob/three.js #34806](https://github.com/mrdoob/three.js/pull/34806) — merged 2026-10-05T12:51:36Z by [Mugen87](https://github.com/Mugen87); [actual merge commit `1e721b19`](https://github.com/mrdoob/three.js/commit/1e721b192009fbdd880bd1b2609ab10559045371).
  - [Final `examples/jsm/math/ColorConverter.js`](https://github.com/mrdoob/three.js/blob/1e721b192009fbdd880bd1b2609ab10559045371/examples/jsm/math/ColorConverter.js)
  - [Final `test/unit/addons/math/ColorConverter.tests.js`](https://github.com/mrdoob/three.js/blob/1e721b192009fbdd880bd1b2609ab10559045371/test/unit/addons/math/ColorConverter.tests.js)
  - [Final `test/unit/three.addons.unit.js`](https://github.com/mrdoob/three.js/blob/1e721b192009fbdd880bd1b2609ab10559045371/test/unit/three.addons.unit.js)
