# Three algorithm correctness fixes

These changes repair observable incorrect results and an unreachable-path crash in existing Python implementations.

## Jaro–Winkler: consume matched positions correctly

The matcher replaced consumed characters with literal spaces and searched for a character's first occurrence outside the current matching slice. Literal spaces and repeated characters could therefore consume the wrong position. The merged implementation tracks character positions in deques and consumes an available position within the matching window. Landed doctests cover spaces and repeated characters, including `jaro_winkler("aa ", "aa")` rounding to `0.911111`.

## Bidirectional A*: stop when either frontier is exhausted

The search popped from both frontiers while its loop continued if either frontier was nonempty. An isolated endpoint could empty one frontier first and trigger a pop from an empty list. The loop now requires both frontiers to remain available. Landed doctests cover isolated endpoints, simultaneous exhaustion and a reachable corridor. The existing start-only fallback for an unreachable route is preserved.

## Maximum Fenwick tree: retain the maximum after updates

Updating a smaller sibling could overwrite a cached maximum using array indices rather than the values in its bucket. The fix preserves unaffected maxima and recomputes affected buckets when their maximum decreases. Landed doctests cover sibling updates, decreases and an ancestor's own value. One example updates index 4 to 20 and index 5 to 1; querying `[0, 6)` must still return 20.

## Validation and limits

Each final merged Python module includes its regression doctests and an opt-in benchmark. These are correctness fixes; this case study makes no general speedup claim. The final PRs each received an APPROVED review from cclauss before being merged.

## Upstream evidence

- [TheAlgorithms/Python #15483](https://github.com/TheAlgorithms/Python/pull/15483) — merged 2026-10-03T07:24:27Z by [cclauss](https://github.com/cclauss); [actual merge commit `ef2ecc4d`](https://github.com/TheAlgorithms/Python/commit/ef2ecc4d34d17ce6249ba5d3f3c17822dfd7bd50).
  - [Final `strings/jaro_winkler.py`](https://github.com/TheAlgorithms/Python/blob/ef2ecc4d34d17ce6249ba5d3f3c17822dfd7bd50/strings/jaro_winkler.py)
- [TheAlgorithms/Python #15484](https://github.com/TheAlgorithms/Python/pull/15484) — merged 2026-10-03T05:54:24Z by [cclauss](https://github.com/cclauss); [actual merge commit `29f9da7f`](https://github.com/TheAlgorithms/Python/commit/29f9da7f202a3909e6156b65a36ebca4d04001f9).
  - [Final `graphs/bidirectional_a_star.py`](https://github.com/TheAlgorithms/Python/blob/29f9da7f202a3909e6156b65a36ebca4d04001f9/graphs/bidirectional_a_star.py)
- [TheAlgorithms/Python #15485](https://github.com/TheAlgorithms/Python/pull/15485) — merged 2026-10-03T07:20:53Z by [cclauss](https://github.com/cclauss); [actual merge commit `875082ad`](https://github.com/TheAlgorithms/Python/commit/875082adbcc8a197fe98e948df57194ee8a78e6d).
  - [Final `data_structures/binary_tree/maximum_fenwick_tree.py`](https://github.com/TheAlgorithms/Python/blob/875082adbcc8a197fe98e948df57194ee8a78e6d/data_structures/binary_tree/maximum_fenwick_tree.py)
