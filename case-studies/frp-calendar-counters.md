# Rotate daily counters by calendar date across DST

## Problem

The daily counter measured the interval between local midnights in elapsed 24-hour units. Daylight-saving transitions can create 23-hour days, 25-hour days or a nonexistent local midnight, so this arithmetic could retain or rotate the wrong date bucket.

## Change

The counter extracts the current local year, month and day and represents that date at midnight UTC for day arithmetic. This preserves the local calendar label while making adjacent labels exactly one day apart; it does not convert the original instant into a different user's local date.

## Validation in the merged change

Clock-controlled tests cover New York spring and autumn transitions, multiple-day retention and expiry, and São Paulo's skipped midnight. Production code and tests both landed. fatedier merged the PR; the public review collection does not contain a separate APPROVED review.

## Upstream evidence

- [fatedier/frp #5555](https://github.com/fatedier/frp/pull/5555) — merged 2026-10-09T12:13:04Z by [fatedier](https://github.com/fatedier); [actual merge commit `ab095986`](https://github.com/fatedier/frp/commit/ab0959868ad8848aa15861f66f6fb30f0814f529).
  - [Final `pkg/util/metric/date_counter.go`](https://github.com/fatedier/frp/blob/ab0959868ad8848aa15861f66f6fb30f0814f529/pkg/util/metric/date_counter.go)
  - [Final `pkg/util/metric/date_counter_test.go`](https://github.com/fatedier/frp/blob/ab0959868ad8848aa15861f66f6fb30f0814f529/pkg/util/metric/date_counter_test.go)
