# Refresh a mode list after the active request completes

## Problem

A monitor update could arrive while MAVSDK was downloading available modes. Starting the replacement request before the active request finished could encounter `Busy` and leave the list refresh incomplete.

## Change

The implementation records the pending monitor sequence, waits for the current request to finish, discards its stale reply and restarts the download. It also handles replies that omit their sequence number.

## Validation and scope

The merged system test controls message ordering and covers both sequenced replies and replies without a sequence. Five exact-head workflows succeeded: Linux, macOS, Windows, Kotlin and fuzzing.

A separate two-client, transport-stubbed probe raised a possible multi-instance interaction. It did not reproduce a live SDK or production failure, and the scope question remained unanswered before merge. This entry does not claim that case is resolved.

## Upstream evidence

[MAVSDK #3214](https://github.com/mavlink/MAVSDK/pull/3214) was approved and merged by julianoes on 10 November 2026 at [commit `3eea18c`](https://github.com/mavlink/MAVSDK/commit/3eea18ca99edc7a0087e0e5e4b2bffbcfb376b28). The maintainer-created squash commit records a different author email from my preferred contribution email.
