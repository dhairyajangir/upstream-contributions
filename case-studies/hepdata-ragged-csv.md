# Preserve rows with missing values in CSV exports

## Problem

A HEPData table can have dependent columns with fewer values than the independent column. CSV conversion indexed every column as if it had the same length, raising an error when a value was missing.

## Change

The CSV writer iterates over all columns with `zip_longest` and fills missing values with empty strings. A table with three independent values and shorter dependent columns retains all three rows instead of failing.

## Validation and scope

The merged regression covers missing dependent values in both packed and unpacked CSV output. The exact-head upstream CI test passed; its deploy job was skipped. An independent local container run passed 51 tests; its dependencies were not lock-pinned. The regression failed against the previous writer in a separate base control.

This addresses the CSV portion of [issue #44](https://github.com/HEPData/hepdata-converter/issues/44); it does not claim a fix for ROOT or YODA. HEPData is a Durham–CERN scientific data service; this is an established scientific-upstream contribution, not a 100,000-star or corporate repository claim.

## Upstream evidence

[HEPData/hepdata-converter #72](https://github.com/HEPData/hepdata-converter/pull/72) was approved and merged by GraemeWatt on 11 November 2026 at [commit `b47043e`](https://github.com/HEPData/hepdata-converter/commit/b47043eda0e4b180c6b23538caedeedfb69f3019). The contributor commit uses GitHub’s noreply email rather than my preferred contribution email.
