# Restore a hovered calorimeter cell when selection is disabled

## Problem

Phoenix highlights a hovered instanced calorimeter cell in white. Disabling object selection while the cell was hovered cleared ordinary outlines and selections, but left that cell white instead of restoring its original color.

## Change

The selection shutdown path calls the existing `clearInstanceHighlight()` helper. This restores the saved per-instance color and clears the cached highlight before the other selection cleanup runs. The production fix adds one line.

## Validation in the merged change

The source fix and regression test file both landed. Two parameterized cases cover instance indices zero and one in a real two-cell `InstancedMesh`. They verify the white hover state, restoration of the original color array—including the neighboring cell—and an increment to the color attribute's update version. The renderer is mocked; full browser/GPU appearance and the complete pointer/toggle interaction remain unverified.

Upstream Node 20 CI passed, along with smoke and commit/title checks. The PR description separately discloses the local Node 22 full-suite result: 659 passed, two failed and seven skipped. The failures involved a compression-test deadline and a random-color uniqueness assertion; their causes were not established by the inspected scope evidence. No test timeout, assertion or CI gate was relaxed.

HSF member EdwardMoyse merged the PR and thanked the contributor. There was no separate formal APPROVED review.

## Scope of this entry

Phoenix is a smaller scientific project: it had 88 stars when verified on 31 October. This contribution was submitted on 18 October and merged on 25 October.

## Upstream evidence

- [HSF/phoenix #1045](https://github.com/HSF/phoenix/pull/1045) — merged 2026-10-25T17:02:21Z by [EdwardMoyse](https://github.com/EdwardMoyse); [actual merge commit `4fbd3790`](https://github.com/HSF/phoenix/commit/4fbd3790aa79573018ca3b4c29b9a22b9309b1f0).
  - [Final `packages/phoenix-event-display/src/managers/three-manager/selection-manager.ts`](https://github.com/HSF/phoenix/blob/4fbd3790aa79573018ca3b4c29b9a22b9309b1f0/packages/phoenix-event-display/src/managers/three-manager/selection-manager.ts)
  - [Final `packages/phoenix-event-display/src/tests/managers/three-manager/selection-manager.test.ts`](https://github.com/HSF/phoenix/blob/4fbd3790aa79573018ca3b4c29b9a22b9309b1f0/packages/phoenix-event-display/src/tests/managers/three-manager/selection-manager.test.ts)
  - [Maintainer's acceptance](https://github.com/HSF/phoenix/pull/1045#issuecomment-6400532835)
