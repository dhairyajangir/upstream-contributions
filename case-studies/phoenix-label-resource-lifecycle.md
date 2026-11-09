# Release Phoenix label resources when a label goes away

## Problem

Phoenix orients label text toward the camera with a listener on the controls. Removing a label could leave its listener and text resources behind. Replacing a label after an event rebuild could also leave a listener on the old controls because the event object's UUID had changed.

## Change

The scene manager stores a cleanup function for each label ID. It captures the original controls and callback, so removal, replacement and event clearing can unsubscribe the right listener and dispose the text geometry and material. Cleanup looks only in the label group to avoid disposing an event object with the same name.

## Validation in the merged change

Both submitted file blobs match the files in the upstream merge. Four regression tests cover removal with a same-named event object, replacement on different controls, replacement on a different UUID, and repeated event rebuilds. They use actual Three.js text geometry and OrbitControls, checking disposal and listener cleanup while leaving unrelated listeners intact.

The submitted head passed upstream Node 20 build and tests, smoke tests, and title and commit-message checks. Local validation recorded 667 passing tests and seven skipped. This work did not measure GPU memory or validate a browser interaction.

## Upstream evidence

- [HSF/phoenix #1051](https://github.com/HSF/phoenix/pull/1051) — merged 1 November 2026 by [EdwardMoyse](https://github.com/EdwardMoyse); [merge commit](https://github.com/HSF/phoenix/commit/b2ae18218b6d63addbcb9b5c9abf253d00e450d2).
- [Merged implementation](https://github.com/HSF/phoenix/blob/b2ae18218b6d63addbcb9b5c9abf253d00e450d2/packages/phoenix-event-display/src/managers/three-manager/scene-manager.ts) and [regressions](https://github.com/HSF/phoenix/blob/b2ae18218b6d63addbcb9b5c9abf253d00e450d2/packages/phoenix-event-display/src/tests/managers/three-manager/label-lifecycle.test.ts).
- [Node 20 CI](https://github.com/HSF/phoenix/actions/runs/41287785469), [smoke tests](https://github.com/HSF/phoenix/actions/runs/41287785529) and [maintainer's comment](https://github.com/HSF/phoenix/pull/1051#issuecomment-6561381954).
