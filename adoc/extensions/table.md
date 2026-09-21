# `sycl_khr_*` extensions

Dates derived from `git log` history of the extension documents in
`adoc/extensions/`, including the heads of all GitHub pull requests (see
[Methodology](#methodology)). "Created" is the author date of the commit that
first added the document on its development branch (following renames);
"Merged" is the date the document landed on `main`, and "Adding commit" is the
commit on `main` that introduced it.

## Published (on `main`)

| Extension | Created | Merged into `main` | Adding commit | PR |
| --- | --- | --- | --- | --- |
| `sycl_khr_default_context` | 2024-09-17 | 2024-11-14 | [`333e895`](https://github.com/KhronosGroup/SYCL-Docs/commit/333e8956f7b099b4b45b3ffba4ca440f20968987) | [#624](https://github.com/KhronosGroup/SYCL-Docs/pull/624) |
| `sycl_khr_group_interface` | 2024-10-04 | 2025-05-29 | [`d903d2f`](https://github.com/KhronosGroup/SYCL-Docs/commit/d903d2f3b7d5d9e17cc3ffe6671faa926aa138c3) | [#638](https://github.com/KhronosGroup/SYCL-Docs/pull/638) |
| `sycl_khr_dynamic_addrspace_cast` | 2024-10-25 | 2025-10-16 | [`fac9b20`](https://github.com/KhronosGroup/SYCL-Docs/commit/fac9b206e1d5ccb9ef8ef190cf81c3eed62a0b3c) | [#650](https://github.com/KhronosGroup/SYCL-Docs/pull/650) |
| `sycl_khr_static_addrspace_cast` | 2024-11-12 | 2025-10-16 | [`fac9b20`](https://github.com/KhronosGroup/SYCL-Docs/commit/fac9b206e1d5ccb9ef8ef190cf81c3eed62a0b3c) | [#650](https://github.com/KhronosGroup/SYCL-Docs/pull/650) |
| `sycl_khr_work_item_queries` | 2024-12-16 | 2025-10-03 | [`35b4ece`](https://github.com/KhronosGroup/SYCL-Docs/commit/35b4ece3992e0d36fe9826f21b164b32aed51d5d) | [#682](https://github.com/KhronosGroup/SYCL-Docs/pull/682) |
| `sycl_khr_queue_empty_query` | 2025-01-28 | 2025-05-15 | [`c90cf7b`](https://github.com/KhronosGroup/SYCL-Docs/commit/c90cf7b385b622c4d4295ef8f93eae5253855d27) | [#700](https://github.com/KhronosGroup/SYCL-Docs/pull/700) |
| `sycl_khr_max_work_group_queries` | 2025-02-11 | 2025-06-19 | [`aaa3ee5`](https://github.com/KhronosGroup/SYCL-Docs/commit/aaa3ee5bdfa331837b1e1ce657c67d3900d48b30) | [#712](https://github.com/KhronosGroup/SYCL-Docs/pull/712) |
| `sycl_khr_split_headers` | 2025-04-18 | 2026-08-06 | [`0e2ded4`](https://github.com/KhronosGroup/SYCL-Docs/commit/0e2ded40265ef5af492a63fd9857150f7888c622) | [#814](https://github.com/KhronosGroup/SYCL-Docs/pull/814) |
| `sycl_khr_queue_flush` | 2025-05-05 | 2025-08-14 | [`9ffe540`](https://github.com/KhronosGroup/SYCL-Docs/commit/9ffe54021c7252bcbbe55f75b009b9aaf744baee) | [#809](https://github.com/KhronosGroup/SYCL-Docs/pull/809) |

## Proposed but not on `main`

Extensions proposed in pull requests (mostly from forks) that have not landed.
"Created" is again the first commit adding the document; "Age / resolved" is
days open as of 2026-09-21 for live proposals, or the close date for dead ones.

| Extension | Created | State | Age / resolved | PR(s) |
| --- | --- | --- | --- | --- |
| `sycl_khr_launch` | 2024-10-17 | open | 704 days | [#922](https://github.com/KhronosGroup/SYCL-Docs/pull/922) (earlier [#644](https://github.com/KhronosGroup/SYCL-Docs/pull/644), [#921](https://github.com/KhronosGroup/SYCL-Docs/pull/921)) |
| `sycl_khr_properties` | 2026-02-06 | open (draft) | 227 days | [#980](https://github.com/KhronosGroup/SYCL-Docs/pull/980) |
| `sycl_khr_prefetch_host` | 2026-02-12 | open | 221 days | [#960](https://github.com/KhronosGroup/SYCL-Docs/pull/960) |
| `sycl_khr_convert` | 2026-04-04 | open | 170 days | [#995](https://github.com/KhronosGroup/SYCL-Docs/pull/995) |
| `sycl_khr_free_function_kernels` | 2026-06-25 | open | 88 days | [#1033](https://github.com/KhronosGroup/SYCL-Docs/pull/1033) |
| `sycl_khr_command_graph` | 2025-04-21 | closed, unmerged | closed 2025-05-23 | [#825](https://github.com/KhronosGroup/SYCL-Docs/pull/825) |

`sycl_khr_launch` began life as `sycl_khr_free_function_commands` (PR #644,
opened 2024-10-17 by a different author, closed 2026-02-12) and was renamed in
the current PR on 2026-09-14; #921 was opened and closed the same day it was
replaced by #922. It is counted once, from its original 2024-10-17 date.

Two further pull requests added extension documents but are duplicates rather
than distinct proposals, and are excluded from the counts below:
[#1003](https://github.com/KhronosGroup/SYCL-Docs/pull/1003) (a competing branch
for the extension that landed as `sycl_khr_split_headers`, closed 2026-04-22)
and #921 above.

## Development velocity

All figures are as of 2026-09-21, over the 734 days (24.1 months) since the
first extension document was drafted on 2024-09-17. The population is the **15
distinct extensions proposed** to date: 9 published, 5 still in flight, 1
abandoned.

### Per-extension effort and latency

"Latency" is created → merged (or → today for open proposals). "Commits" counts
non-merge commits touching the document; "Post-merge" counts commits touching it
after it landed (maintenance churn). "Lines" is the document's current size.

| Extension | Status | Latency (days) | Commits | Lines | Post-merge commits |
| --- | --- | ---: | ---: | ---: | ---: |
| `sycl_khr_default_context` | published | 58 | 2 | 68 | 4 |
| `sycl_khr_queue_flush` | published | 101 | 9 | 98 | 3 |
| `sycl_khr_queue_empty_query` | published | 107 | 19 | 96 | 8 |
| `sycl_khr_max_work_group_queries` | published | 128 | 47 | 148 | 3 |
| `sycl_khr_group_interface` | published | 237 | 26 | 864 | 4 |
| `sycl_khr_work_item_queries` | published | 291 | 5 | 180 | 5 |
| `sycl_khr_static_addrspace_cast` | published | 338 | 6 | 97 | 3 |
| `sycl_khr_dynamic_addrspace_cast` | published | 356 | 9 | 103 | 4 |
| `sycl_khr_split_headers` | published | 475 | 52 | 650 | 0 |
| `sycl_khr_command_graph` | abandoned | 32 | 4 | 1201 | — |
| `sycl_khr_free_function_kernels` | open | 88 | 16 | 315 | — |
| `sycl_khr_convert` | open | 170 | 1 | 77 | — |
| `sycl_khr_prefetch_host` | open | 221 | 6 | 103 | — |
| `sycl_khr_properties` | open | 227 | 12 | 2377 | — |
| `sycl_khr_launch` | open | 704 | 75 | 1287 | — |
| **Totals** | 9 / 5 / 1 | — | **289** | **7664** | **34** |

### Rates

| Metric | Value |
| --- | --- |
| Submission rate | 15 proposals / 24.1 months = **0.62 per month** (1.87 per quarter) |
| Acceptance (merge) rate | 9 merges / 22.2 months since first merge = **0.41 per month** (1.22 per quarter) |
| Resolution rate (merged + abandoned) | 10 / 24.1 months = **0.41 per month** |
| Net backlog growth | +0.62 − 0.41 = **+0.21 proposals per month** |
| Acceptance ratio | **9 of 10 resolved proposals (90%)** merged, 1 abandoned; **9 of 15 ever submitted (60%)** are published today |
| Time to merge (accepted) | mean **232 days**, median 237, range 58–475 |
| Age of open proposals | mean **282 days**, median 221, max 704 |
| Spec throughput (published) | 2304 lines / 22.2 months = **~104 lines of specification per month** |
| Average work in progress | 3533 open-days / 734 days = **4.8 proposals open concurrently** |
| Peak work in progress | **10 proposals open** on 2025-05-05 |
| Currently open | **5** |
| Unpublished spec text | **5360 lines** in flight or abandoned vs 2304 published (**2.3×**) |
| Post-merge churn | **3.8 follow-up commits** per published extension |

### Interpretation

**The pipeline is not in steady state; the backlog grows.** Proposals arrive at
0.62/month but are resolved at 0.41/month, so roughly one extension per five
months accumulates. Little's Law makes the gap concrete: sustaining the measured
average WIP of 4.8 at a 0.41/month departure rate implies a steady-state latency
of **11.6 months**, considerably worse than the 7.6-month mean latency measured
on the extensions that actually merged. That difference is survivorship bias —
fast proposals merge and enter the latency statistic, while slow ones stay open
and only inflate WIP. `sycl_khr_launch` has now been in flight for 704 days,
1.5× the slowest merge on record.

**Latency is set by review and ratification queueing, not by authoring effort or
document size.** `sycl_khr_dynamic_addrspace_cast` took 356 days with 9 commits
and 103 lines, while the 864-line `sycl_khr_group_interface` merged in 237 days.
`sycl_khr_convert` has been open 170 days on a single commit.

**Most of the specification work written so far is unpublished.** The in-flight
and abandoned documents total 5360 lines against 2304 lines on `main` — the four
largest extension documents ever written (`properties` 2377, `launch` 1287,
`command_graph` 1201, `split_headers` 650) include three that are not published,
and one of those was abandoned outright. Large extensions are where the pipeline
stalls.

**Merges arrive in bursts, not steadily.** 7 of the 9 published extensions landed
in the 154 days from 2025-05-15 to 2025-10-16 (1.4/month), then nothing for 294
days until 2026-08-06. 46 days have passed since the last merge.

### Cadence by quarter

"Backlog" is the number of proposals open at quarter end.

| Quarter | Submitted | Merged | Published (cumulative) | Backlog |
| --- | ---: | ---: | ---: | ---: |
| 2024 Q3 | 1 | 0 | 0 | 1 |
| 2024 Q4 | 5 | 1 | 1 | 5 |
| 2025 Q1 | 2 | 0 | 1 | 7 |
| 2025 Q2 | 3 | 3 | 4 | 6 |
| 2025 Q3 | 0 | 1 | 5 | 5 |
| 2025 Q4 | 0 | 3 | 8 | 2 |
| 2026 Q1 | 2 | 0 | 8 | 4 |
| 2026 Q2 | 2 | 0 | 8 | 6 |
| 2026 Q3 (partial) | 0 | 1 | 9 | 5 |

Submissions came in two waves — 2024 Q3 through 2025 Q2 (11 proposals), then a
277-day drought, then 4 proposals in 2026 Q1–Q2 — while merges are concentrated
in 2025 Q2–Q4. The backlog was drained to 2 at the end of 2025 and has since
climbed back to 5.

## Methodology

Pull request heads were made visible to `git` by adding a refspec to this clone
and refetching:

```sh
git config --add remote.origin.fetch '+refs/pull/*/head:refs/remotes/origin/pr/*'
git fetch origin
```

Candidate proposals were then found by listing `adoc/extensions/` at every
`origin/pr/*` head and keeping documents absent from `main` (733 PR heads, 9
hits). Pull request state, base branch and open/close dates were read from the
GitHub PR pages; the REST API was unavailable (unauthenticated rate limit).
Every candidate targets `KhronosGroup:main`.

### Caveats

* "Created" is a commit author date; "Merged" is the merge commit's date, where
  author and committer date are identical for all 9 merges. 164 of the 1860
  commits on `main` carry a backdated author date, so committer dates were
  checked against author dates throughout; the two differ for three proposals.
  `sycl_khr_split_headers` was drafted 2025-04-18 and its PR opened 2025-05-13;
  `sycl_khr_properties` was authored 2026-02-06 and pushed 2026-02-25; and
  `sycl_khr_convert.adoc` first appears on 2026-04-13, as a rework of work that
  began on its branch on 2026-04-03. Where dates differ the earliest is used as
  the submission date, so these ages are upper bounds by 9–25 days.
* Proposals that were never pushed as a pull request to this repository are
  invisible to this analysis, as are extensions discussed only in the Khronos
  working group.
* 2026 Q3 is incomplete, and activity after 2026-09-21 is not included. Open
  proposals' ages and the WIP figures grow simply with the passage of time.

## Notes

* Both address-space cast extensions come from a single original document,
  `sycl_khr_addrspace_cast.adoc` (added 2024-10-25), which was later split in
  two; the "created" date of `sycl_khr_static_addrspace_cast` is the date of
  that split. Both documents reached `main` in the same merge commit.
* `sycl_khr_split_headers.adoc` was renamed from `sycl_khr_includes.adoc`, and
  `sycl_khr_queue_empty_query.adoc` from `sycl_khr_queue_size_queries.adoc`;
  `--follow` is used throughout so these count as one extension each.
* `sycl_khr_extension_name` appears in the sources but is only a placeholder
  name used by the extension template, not a real extension.
