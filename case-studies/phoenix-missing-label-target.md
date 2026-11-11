# Load remaining saved labels when an event target is missing

## Problem

A saved label can refer to an object absent from the current event. Loading such a label could stop the import before other valid labels were restored.

## Change

The UI manager checks for the target object. If it is absent, it warns and skips that label; it then continues loading the remaining labels.

## Validation and scope

The merged regression saves labels from one synthetic event, loads them into another, and verifies that the stale label is skipped while the valid label remains. The renderer is mocked; this is not a live GPU or full browser validation.

Four exact-head workflow runs succeeded: phoenix-ci, Smoke Test and two Commitlint runs. No formal approval was recorded.

## Upstream evidence

[HSF/Phoenix #1063](https://github.com/HSF/phoenix/pull/1063) was merged by EdwardMoyse on 11 November 2026 at [commit `887133e`](https://github.com/HSF/phoenix/commit/887133ed05c2d5a03af79352f112ea9f74cbbe32). The maintainer-created squash commit records a different author email from my preferred contribution email.
