# `sycl_khr_*` extensions

Dates derived from `git log` history of the extension documents in
`adoc/extensions/`, including the heads of all GitHub pull requests (see
[Methodology](#methodology)). "Created" is the author date of the commit that
first added the document on its development branch (following renames);
"Merged" is the date the document landed on `main`, and "Adding commit" is the
commit on `main` that introduced it.

[Development velocity](#development-velocity) measures the throughput of this
pipeline; [Absorbing the `intel/llvm` extension
backlog](#absorbing-the-intelllvm-extension-backlog) asks how long it would take
that pipeline to standardise the 97 vendor extensions that DPC++ ships today;
and [Composition](#composition-khronos-versus-vendor-extensions) compares the
resulting Khronos/vendor mix with Vulkan's. The Vulkan counterpart of this
analysis is in [`vulkan_table.md`](vulkan_table.md).

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

## Absorbing the `intel/llvm` extension backlog

The `sycl_khr_*` pipeline is fed largely by vendor extensions from
[`intel/llvm`](https://github.com/intel/llvm). That repository keeps its
extension specifications in `sycl/doc/extensions/`, split into `supported`
(stable in DPC++), `experimental`, `proposed`, `deprecated` and `removed`
directories. As of 2026-09-21 the two directories in question hold **97 extensions**
(35 supported, 62 experimental, 44876 lines of specification).
This section estimates how long it would take for all of them to become
Khronos extensions at the rate observed so far.

Five of them have been absorbed into KHR extensions already on `main`, all
under different names, and a sixth was written afterwards against one of them.
None of the renamings is recorded in either repository — the correspondences
below were established by comparing APIs.

### Already landed on `main`, under a different name

| `intel/llvm` extension | Dir | Vendor doc created | Landed as | Merged | Vendor doc → KHR merge | Note |
| --- | --- | --- | --- | --- | ---: | --- |
| `sycl_ext_oneapi_default_context` | supported | 2021-09-10 | [`sycl_khr_default_context`](sycl_khr_default_context.adoc) | 2024-11-14 ([#624](https://github.com/KhronosGroup/SYCL-Docs/pull/624)) | 1161 |  |
| `sycl_ext_oneapi_device_default_context` | supported | 2025-10-27 | [`sycl_khr_default_context`](sycl_khr_default_context.adoc) | 2024-11-14 ([#624](https://github.com/KhronosGroup/SYCL-Docs/pull/624)) | — | written after the KHR extension; the device-level query is still vendor-only |
| `sycl_ext_oneapi_queue_empty` | supported | 2022-12-02 | [`sycl_khr_queue_empty_query`](sycl_khr_queue_empty_query.adoc) | 2025-05-15 ([#700](https://github.com/KhronosGroup/SYCL-Docs/pull/700)) | 895 | `ext_oneapi_empty()` → `queue::khr_empty()` |
| `sycl_ext_oneapi_max_work_group_query` | experimental | 2021-10-18 | [`sycl_khr_max_work_group_queries`](sycl_khr_max_work_group_queries.adoc) | 2025-06-19 ([#712](https://github.com/KhronosGroup/SYCL-Docs/pull/712)) | 1340 |  |
| `sycl_ext_oneapi_prod` | supported | 2022-09-20 | [`sycl_khr_queue_flush`](sycl_khr_queue_flush.adoc) | 2025-08-14 ([#809](https://github.com/KhronosGroup/SYCL-Docs/pull/809)) | 1059 | `ext_oneapi_prod()` → `queue::khr_flush()` |
| `sycl_ext_oneapi_free_function_queries` | supported | 2022-02-03 | [`sycl_khr_work_item_queries`](sycl_khr_work_item_queries.adoc) | 2025-10-03 ([#682](https://github.com/KhronosGroup/SYCL-Docs/pull/682)) | 1338 | `this_work_item::*` → `khr::this_*` |

Five of the nine published `sycl_khr_*` extensions come from this pool, and the
two address-space cast extensions come from `proposed/sycl_ext_oneapi_address_cast`
(`dynamic_address_cast`/`static_address_cast` → `khr::dynamic_addrspace_cast`/
`khr::static_addrspace_cast`), which is outside the supported/experimental set
counted here. Only `sycl_khr_group_interface` and `sycl_khr_split_headers` have no
`intel/llvm` ancestor at all. Counting the in-flight proposals below, **11 of the
15 `sycl_khr_*` proposals ever made (73%) restate an `intel/llvm` extension**.

### Currently in flight

| `intel/llvm` extension | Dir | Vendor doc created | Proposed as | PR | State |
| --- | --- | --- | --- | --- | --- |
| `sycl_ext_oneapi_enqueue_functions` | experimental | 2023-11-10 | `sycl_khr_launch` | [#922](https://github.com/KhronosGroup/SYCL-Docs/pull/922) | open |
| `sycl_ext_oneapi_reusable_events` | experimental | 2025-12-09 | `sycl_khr_launch` | [#922](https://github.com/KhronosGroup/SYCL-Docs/pull/922) | open (event reuse half of the PR) |
| `sycl_ext_oneapi_properties` | experimental | 2022-01-27 | `sycl_khr_properties` | [#980](https://github.com/KhronosGroup/SYCL-Docs/pull/980) | open (draft) |
| `sycl_ext_oneapi_free_function_kernels` | experimental | 2024-01-25 | `sycl_khr_free_function_kernels` | [#1033](https://github.com/KhronosGroup/SYCL-Docs/pull/1033) | open |
| `sycl_ext_oneapi_prefetch` | experimental | 2023-05-30 | `sycl_khr_prefetch_host` | [#960](https://github.com/KhronosGroup/SYCL-Docs/pull/960) | open; covers only device→host prefetch, not the cache-level hints |
| `sycl_ext_oneapi_graph` | experimental | 2023-07-19 | `sycl_khr_command_graph` | [#825](https://github.com/KhronosGroup/SYCL-Docs/pull/825) | closed unmerged 2025-05-23 |

`sycl_khr_prefetch_host` and `sycl_khr_convert` have no `intel/llvm` counterpart,
so the KHR pipeline is not purely an absorption queue.

### The rate of absorption

| Metric | Value |
| --- | --- |
| Pool to absorb | **97** extensions (44876 lines) |
| Absorbed so far | 6 (into 5 KHR extensions) |
| In flight | 5 (into 4 KHR proposals, 1 of them a draft) |
| Attempted and abandoned | 1 (`sycl_ext_oneapi_graph`) |
| Never proposed | **85** (37318 lines) |
| Absorption rate | 6 in 1.85 years since the first KHR merge = **3.24 per year** (0.27/month) |
| Vendor doc → KHR merge latency | n=5, mean **1159 days** (3.2 years), median 1161, range 895–1340 |
| Size ratio of the rewrite | 590 KHR lines from 662 vendor lines = **0.89×** |
| Age of the 85 never-proposed | median **1173 days** (3.2 years), mean 1216, max 2503 |
| Of those, already older than the mean absorption latency | **45 of 85** |

The last two rows are the important ones: the median extension that has never
been proposed to Khronos is already older than the average extension that made
it through, so age alone does not predict absorption. 45 of the 85 have
waited longer than the 3.2 years the successful ones took.

### The pool grows faster than it is absorbed

Reconstructing the contents of the two directories at each year end (the
directory layout itself dates from the 2022-02-01 reorganisation, so the series
starts there):

| Date | `supported` + `experimental` |
| --- | ---: |
| 2022-12-21 | 49 |
| 2023-12-21 | 69 |
| 2024-12-11 | 89 |
| 2025-12-17 | 88 |
| 2026-09-21 | 97 |

That is **+12.8 extensions per year** over the whole period and **+4.5 per year**
over the last 1.8 years, against absorption of 3.2 per year. Even the more
favourable recent growth figure exceeds absorption, and it sits only just below
the total KHR merge throughput of 4.9 extensions per year — so even spending
every single KHR merge on this backlog would barely outpace the arrival of new
vendor extensions.

### Estimates

Two questions have to be separated, because they have very different answers.

**If the pool were frozen today** — no new vendor extensions ever written — the
remaining work divides by the observed rate:

| Scenario | Extensions left | Rate | Time | Completed |
| --- | ---: | --- | ---: | --- |
| Observed absorption rate | 91 | 3.2/yr | **28 years** | 2054 |
| All KHR merge capacity devoted to the backlog | 91 | 4.9/yr | **19 years** | 2045 |
| Observed rate, portable extensions only | 68 | 3.2/yr | **21 years** | 2047 |
| All KHR capacity, portable extensions only | 68 | 4.9/yr | **14 years** | 2040 |

"All KHR merge capacity" means every future `sycl_khr_*` merge, at the measured
0.41 merges/month, restates an `intel/llvm` extension and nothing else —
`sycl_khr_split_headers`, `sycl_khr_group_interface`, `sycl_khr_convert` and
`sycl_khr_prefetch_host` show that is not what happens. "Portable extensions
only" excludes the 23 that are vendor- or backend-scoped by construction
(16 `sycl_ext_intel_*`, 2 `sycl_ext_codeplay_*`, and 5 `sycl_ext_oneapi_*` bound to
Level Zero, CUDA, ESIMD or a vendor device-architecture enumeration), on the
assumption that these would never become Khronos extensions under any name.

**Accounting for new arrivals**, the answer changes character. With the pool
growing at +4.5/year and absorption at 3.2/year, the backlog never drains — it
grows by 1.3 extensions per year. Absorption would have to reach
4.5/year merely to hold the line, and **13.6/year — 2.8× the entire current
KHR merge throughput — to clear the present backlog within ten years.** At full
current KHR capacity (4.9/year) against +4.5/year of arrivals, the net drain is
0.4/year and the 91 remaining extensions would take 229 years.

So the defensible answer to "when can all supported and experimental extensions
be added as Khronos extensions" is:

* **~28 years (around 2054)** for the 91 that exist today, at the rate
  actually observed over the last two years;
* **~14 years (around 2040)** in the most optimistic case that is still
  consistent with the data — vendor-specific extensions excluded and every KHR
  merge slot spent on the backlog;
* **never**, if `intel/llvm` keeps adding extensions at its recent rate and
  Khronos keeps merging at 0.41/month.

The dominant term is not the size of the backlog but the ratio of the two rates,
and they are currently the wrong way round. The next subsection asks what happens
if that ratio is inverted by raising KHR throughput to Vulkan's.

A cross-check on volume agrees. The 85 never-proposed documents are
37318 lines; at the 0.89× rewrite ratio measured above that is about
33213 lines of KHR specification, and `main` has gained published
extension text at 104 lines per month, which is 27 years of output.

### What matching Vulkan's `KHR` rate would change

Vulkan publishes Khronos extensions at **15.6 per year** over its whole history
and **12.7 per year** since 2018 (see
[`vulkan_table.md`](vulkan_table.md#khronos-khr-publication-rate)). SYCL's
measured rate is **4.9 per year**. Matching Vulkan therefore means a **2.6× to
3.2× increase** in KHR throughput.

Throughput has to be converted into absorptions. Of the 9 published
`sycl_khr_*` extensions, 5 absorbed 6 extensions from the
`supported`/`experimental` pool — a yield of **0.67 pool extensions per published
KHR extension**. Holding that yield fixed:

| KHR publication rate | Absorptions/yr | 91 left, frozen pool | 68 portable, frozen pool | 91 left, pool still growing +4.5/yr |
| --- | ---: | ---: | ---: | ---: |
| 4.9/yr (SYCL today) | 3.3 | 28 yr (2054) | 21 yr (2047) | **never** (net −1.3/yr) |
| 12.7/yr (Vulkan since 2018) | 8.5 | **11 yr (2037)** | 8 yr (2034) | **23 yr (2049)** |
| 15.6/yr (Vulkan all time) | 10.4 | **9 yr (2035)** | 7 yr (2033) | **15 yr (2041)** |

The qualitative change is the sign of the balance. Today absorption (3.3/yr) is
below the pool's net growth (+4.5/yr), so the backlog never drains and the
estimate is not a number but "never". At either Vulkan rate absorption exceeds
growth — by 4.0/yr or 5.9/yr — and the problem becomes finite: **the backlog
clears in roughly 15 to 23 years including all future arrivals, or 9 to 11 years
if `intel/llvm` stopped adding extensions today.** That is the single most
important effect; the absolute durations matter less than crossing from a
diverging to a converging regime.

If every KHR extension restated a pool extension (yield 1.0 instead of 0.67 —
not what happens, but the upper bound):

| KHR publication rate | 91 left, frozen pool | 91 left, pool growing +4.5/yr |
| --- | ---: | ---: |
| 4.9/yr | 19 yr (2045) | 228 yr |
| 12.7/yr | 7 yr (2033) | **11 yr (2037)** |
| 15.6/yr | 6 yr (2032) | **8 yr (2034)** |

The volume cross-check agrees. The 85 never-proposed documents are 37318 lines,
about 33213 lines of KHR text at the measured 0.89× rewrite ratio. Published
extension text currently accumulates at 104 lines/month; scaled by 2.6–3.2× that
is 270–331 lines/month, or **8 to 10 years** of output, against 27 years today.

Two things this does *not* fix:

* **Per-extension latency.** The five absorbed extensions took a mean of 1159
  days (3.2 years) from vendor document to KHR merge, and the nine published
  extensions took a mean of 232 days from first draft to merge. Higher throughput
  shrinks the queueing part of that wait, not the drafting and review part, so
  no individual extension arrives much faster than ~8 months.
* **The 23 vendor-scoped extensions.** `sycl_ext_intel_esimd`,
  `sycl_ext_oneapi_backend_level_zero` and the rest are bound to one vendor or
  backend by construction. Even at Vulkan's rate they are not candidates, which
  is why the "68 portable" column is the more meaningful target.

What it would take. At the measured mean latency of 232 days, Little's Law puts
the required work in progress at **8 to 10 concurrent proposals** (15.6 × 0.635)
versus the 4.8 average observed so far — though SYCL has already peaked at 10 open
proposals, on 2025-05-05, so the pipeline has held that much work once. The
alternative to more concurrency is faster turnaround: sustaining 15.6/yr at
today's average WIP of 4.8 would require median time-to-merge to fall from 237
days to about **112 days**.

Finally, matching Vulkan in absolute terms is a much larger relative ask. Vulkan's
15.6/yr is 3.1% of its 504-extension surface per year; 15.6/yr for SYCL would be
**15% of its 106-extension surface per year**. Judged relatively, SYCL matching
Vulkan would mean roughly 3.3 KHR extensions per year — which is below what it
already does. The absolute figure is the right target only because the backlog to
absorb is an absolute count of documents, not a fraction.

The effect on composition is correspondingly large. With KHR output at 12.7–15.6
per year against 11.0 new vendor extensions per year, the Khronos share of the
SYCL extension surface converges to **54–59%** rather than the 29–31% implied by
current rates, and passes Vulkan's 33% in **4 to 5 years** (around 2030–2031)
instead of never — see [Composition](#composition-khronos-versus-vendor-extensions).

### Appendix: the 85 extensions never proposed to Khronos

"Scope" marks extensions that are vendor- or backend-specific by construction.
Age is from the first commit of the specification document in `intel/llvm`.

| # | `intel/llvm` extension | Dir | Scope | Created | Age (y) | Lines |
| ---: | --- | --- | --- | --- | ---: | ---: |
| 1 | `sycl_ext_intel_kernel_args_restrict` | supported | vendor | 2019-11-14 | 6.9 | 134 |
| 2 | `sycl_ext_oneapi_enqueue_barrier` | supported | portable | 2020-03-18 | 6.5 | 325 |
| 3 | `sycl_ext_intel_esimd` | supported | vendor | 2020-07-20 | 6.2 | 1161 |
| 4 | `sycl_ext_oneapi_use_pinned_host_memory_property` | supported | portable | 2020-07-22 | 6.2 | 39 |
| 5 | `sycl_ext_oneapi_local_memory` | supported | portable | 2020-08-19 | 6.1 | 205 |
| 6 | `sycl_ext_oneapi_accessor_properties` | supported | portable | 2020-09-08 | 6.0 | 513 |
| 7 | `sycl_ext_oneapi_filter_selector` | supported | portable | 2020-09-18 | 6.0 | 86 |
| 8 | `sycl_ext_oneapi_dot_accumulate` | supported | portable | 2020-11-04 | 5.9 | 112 |
| 9 | `sycl_ext_oneapi_backend_level_zero` | supported | vendor | 2021-01-29 | 5.6 | 675 |
| 10 | `sycl_ext_oneapi_group_sort` | experimental | portable | 2021-04-28 | 5.4 | 1223 |
| 11 | `sycl_ext_oneapi_invoke_simd` | experimental | vendor | 2021-05-04 | 5.4 | 469 |
| 12 | `sycl_ext_oneapi_uniform` | experimental | portable | 2021-05-04 | 5.4 | 201 |
| 13 | `sycl_ext_oneapi_assert` | supported | portable | 2021-05-31 | 5.3 | 162 |
| 14 | `sycl_ext_oneapi_srgb` | supported | portable | 2021-07-16 | 5.2 | 154 |
| 15 | `sycl_ext_oneapi_sub_group_mask` | supported | portable | 2021-08-18 | 5.1 | 369 |
| 16 | `sycl_ext_oneapi_device_global` | experimental | portable | 2021-09-29 | 5.0 | 1213 |
| 17 | `sycl_ext_oneapi_kernel_properties` | experimental | portable | 2021-10-19 | 4.9 | 475 |
| 18 | `sycl_ext_oneapi_discard_queue_events` | supported | portable | 2021-11-23 | 4.8 | 15 |
| 19 | `sycl_ext_oneapi_sub_group` | supported | portable | 2022-02-02 | 4.6 | 5 |
| 20 | `sycl_ext_oneapi_native_math` | experimental | portable | 2022-03-10 | 4.5 | 112 |
| 21 | `sycl_ext_oneapi_usm_device_read_only` | supported | portable | 2022-03-22 | 4.5 | 98 |
| 22 | `sycl_ext_oneapi_auto_local_range` | experimental | portable | 2022-04-04 | 4.5 | 204 |
| 23 | `sycl_ext_oneapi_cuda_async_barrier` | experimental | vendor | 2022-05-17 | 4.3 | 390 |
| 24 | `sycl_ext_oneapi_root_group` | experimental | portable | 2022-06-10 | 4.3 | 789 |
| 25 | `sycl_ext_oneapi_device_architecture` | experimental | vendor | 2022-11-03 | 3.9 | 1275 |
| 26 | `sycl_ext_oneapi_memcpy2d` | supported | portable | 2022-11-04 | 3.9 | 231 |
| 27 | `sycl_ext_oneapi_bfloat16` | supported | portable | 2022-11-28 | 3.8 | 358 |
| 28 | `sycl_ext_oneapi_bfloat16_math_functions` | experimental | portable | 2022-11-28 | 3.8 | 649 |
| 29 | `sycl_ext_oneapi_queue_priority` | supported | portable | 2022-11-29 | 3.8 | 108 |
| 30 | `sycl_ext_oneapi_weak_object` | supported | portable | 2022-12-05 | 3.8 | 334 |
| 31 | `sycl_ext_intel_cslice` | supported | vendor | 2022-12-09 | 3.8 | 275 |
| 32 | `sycl_ext_intel_queue_index` | supported | vendor | 2022-12-09 | 3.8 | 210 |
| 33 | `sycl_ext_oneapi_user_defined_reductions` | experimental | portable | 2022-12-13 | 3.8 | 224 |
| 34 | `sycl_ext_oneapi_annotated_ptr` | experimental | portable | 2022-12-15 | 3.8 | 817 |
| 35 | `sycl_ext_oneapi_kernel_arg_properties` | experimental | portable | 2022-12-15 | 3.8 | 233 |
| 36 | `sycl_ext_oneapi_non_uniform_groups` | experimental | portable | 2023-02-01 | 3.6 | 662 |
| 37 | `sycl_ext_oneapi_peer_access` | supported | portable | 2023-03-03 | 3.6 | 165 |
| 38 | `sycl_ext_oneapi_cuda_tex_cache_read` | experimental | vendor | 2023-03-08 | 3.5 | 119 |
| 39 | `sycl_ext_intel_cache_config` | experimental | vendor | 2023-03-27 | 3.5 | 248 |
| 40 | `sycl_ext_intel_legacy_image` | supported | vendor | 2023-05-05 | 3.4 | 112 |
| 41 | `sycl_ext_codeplay_max_registers_per_work_group_query` | experimental | vendor | 2023-05-12 | 3.4 | 56 |
| 42 | `sycl_ext_intel_grf_size` | experimental | vendor | 2023-06-14 | 3.3 | 254 |
| 43 | `sycl_ext_oneapi_bindless_images` | experimental | portable | 2023-07-06 | 3.2 | 2853 |
| 44 | `sycl_ext_intel_queue_immediate_command_list` | supported | vendor | 2023-07-13 | 3.2 | 157 |
| 45 | `sycl_ext_oneapi_copy_optimize` | experimental | portable | 2023-07-19 | 3.2 | 159 |
| 46 | `sycl_ext_oneapi_complex` | experimental | portable | 2023-07-27 | 3.2 | 580 |
| 47 | `sycl_ext_oneapi_forward_progress` | experimental | portable | 2023-08-25 | 3.1 | 502 |
| 48 | `sycl_ext_intel_matrix` | experimental | vendor | 2023-08-28 | 3.1 | 647 |
| 49 | `sycl_ext_oneapi_matrix` | experimental | portable | 2023-08-28 | 3.1 | 1411 |
| 50 | `sycl_ext_intel_cache_controls` | experimental | vendor | 2023-09-11 | 3.0 | 370 |
| 51 | `sycl_ext_oneapi_kernel_compiler` | experimental | portable | 2023-11-10 | 2.9 | 1399 |
| 52 | `sycl_ext_oneapi_kernel_compiler_opencl` | experimental | portable | 2023-11-10 | 2.9 | 484 |
| 53 | `sycl_ext_intel_fp_control` | experimental | vendor | 2023-11-16 | 2.8 | 166 |
| 54 | `sycl_ext_oneapi_raw_kernel_arg` | experimental | portable | 2023-12-08 | 2.8 | 162 |
| 55 | `sycl_ext_oneapi_kernel_compiler_spirv` | experimental | portable | 2023-12-20 | 2.8 | 344 |
| 56 | `sycl_ext_oneapi_composite_device` | experimental | portable | 2023-12-21 | 2.8 | 288 |
| 57 | `sycl_ext_oneapi_in_order_queue_events` | experimental | portable | 2024-01-15 | 2.7 | 156 |
| 58 | `sycl_ext_oneapi_profiling_tag` | experimental | portable | 2024-01-18 | 2.7 | 208 |
| 59 | `sycl_ext_oneapi_private_alloca` | experimental | portable | 2024-02-28 | 2.6 | 299 |
| 60 | `sycl_ext_intel_esimd_functions` | supported | vendor | 2024-03-22 | 2.5 | 998 |
| 61 | `sycl_ext_oneapi_group_load_store` | experimental | portable | 2024-04-04 | 2.5 | 644 |
| 62 | `sycl_ext_oneapi_work_group_memory` | experimental | portable | 2024-06-07 | 2.3 | 559 |
| 63 | `sycl_ext_oneapi_virtual_mem` | experimental | portable | 2024-07-01 | 2.2 | 422 |
| 64 | `sycl_ext_codeplay_enqueue_native_command` | experimental | vendor | 2024-07-22 | 2.2 | 447 |
| 65 | `sycl_ext_oneapi_reduction_properties` | experimental | portable | 2024-09-03 | 2.0 | 254 |
| 66 | `sycl_ext_oneapi_tangle` | experimental | portable | 2024-10-04 | 2.0 | 375 |
| 67 | `sycl_ext_oneapi_get_kernel_info` | supported | portable | 2024-10-08 | 2.0 | 225 |
| 68 | `sycl_ext_intel_event_mode` | experimental | vendor | 2024-10-31 | 1.9 | 166 |
| 69 | `sycl_ext_oneapi_device_image_backend_content` | experimental | portable | 2024-12-03 | 1.8 | 250 |
| 70 | `sycl_ext_oneapi_work_group_scratch_memory` | experimental | portable | 2024-12-04 | 1.8 | 189 |
| 71 | `sycl_ext_oneapi_work_group_static` | experimental | portable | 2024-12-04 | 1.8 | 236 |
| 72 | `sycl_ext_oneapi_num_compute_units` | supported | portable | 2024-12-11 | 1.8 | 174 |
| 73 | `sycl_ext_oneapi_current_device` | experimental | portable | 2025-01-15 | 1.7 | 141 |
| 74 | `sycl_ext_intel_kernel_queries` | supported | vendor | 2025-03-06 | 1.5 | 139 |
| 75 | `sycl_ext_oneapi_memory_export` | experimental | portable | 2025-07-22 | 1.2 | 362 |
| 76 | `sycl_ext_oneapi_clock` | experimental | portable | 2025-09-05 | 1.0 | 196 |
| 77 | `sycl_ext_oneapi_platform_device_index` | supported | portable | 2025-09-12 | 1.0 | 197 |
| 78 | `sycl_ext_oneapi_device_is_integrated_gpu` | experimental | portable | 2025-10-02 | 1.0 | 111 |
| 79 | `sycl_ext_oneapi_usm_shortcuts` | experimental | portable | 2025-10-03 | 1.0 | 366 |
| 80 | `sycl_ext_oneapi_device_wait` | experimental | portable | 2025-10-14 | 0.9 | 197 |
| 81 | `sycl_ext_oneapi_fp8` | experimental | portable | 2025-11-13 | 0.9 | 1587 |
| 82 | `sycl_ext_oneapi_inter_process_communication` | experimental | portable | 2025-11-20 | 0.8 | 1432 |
| 83 | `sycl_ext_intel_device_info` | supported | vendor | 2026-02-23 | 0.6 | 1449 |
| 84 | `sycl_ext_oneapi_register_host_memory` | experimental | portable | 2026-06-23 | 0.2 | 311 |
| 85 | `sycl_ext_intel_maximum_registers` | experimental | vendor | 2026-08-03 | 0.1 | 247 |


## Composition: Khronos versus vendor extensions

The Vulkan registry splits 33% Khronos (`KHR`) / 31% multi-vendor (`EXT`) / 36%
single-vendor. SYCL has no equivalent of the `EXT` tier — there is no
cross-vendor-but-not-Khronos namespace with independent implementations behind it
— so the comparison collapses to Khronos versus vendor. On that basis the Vulkan
proportion is 33% / 67%.

SYCL does not match it. Counting everything a DPC++ application can use today,
the 9 published `sycl_khr_*` extensions against the 97 vendor extensions in
`intel/llvm` give:

| Population | n | Khronos | Vendor |
| --- | ---: | ---: | ---: |
| Vulkan, all ever published | 504 | 165 (**33%**) | 339 (67%) |
| Vulkan, live today | 483 | 151 (**31%**) | 332 (69%) |
| SYCL: `sycl_khr_*` + `intel/llvm` supported/experimental | 106 | 9 (**8.5%**) | 97 (91.5%) |
| SYCL: including removed and deprecated documents, and all 15 KHR proposals | 152 | 15 (**9.9%**) | 137 (90.1%) |

The Khronos share of the SYCL extension surface is **8.5%, roughly a quarter of
Vulkan's 33%**. Within the vendor 91.5%, the breakdown is 79 `sycl_ext_oneapi_*`
(74.5% of everything), 16 `sycl_ext_intel_*` (15.1%) and 2 `sycl_ext_codeplay_*`.
`oneapi` is the closest thing SYCL has to Vulkan's `EXT` tier, but it is not the
same thing: it is a single vendor's umbrella specification implemented by a single
compiler, not a namespace requiring agreement between vendors, which is why
collapsing it into "vendor" is the right call.

Adoption is not the constraint. `intel/llvm` implements all 9 published
extensions (`sycl/include/sycl/khr/` plus `queue::khr_empty`/`khr_flush`), so
every `sycl_khr_*` extension that exists is shipped by the implementation that
produced most of the vendor extensions. The 8.5% measures how much of that
implementation's surface has been standardised, not how much of the standard has
been implemented.

### The stock differs; the flow does not

The 33% figure is a ten-year accumulation, whereas SYCL's KHR effort is two years
old and its vendor extensions are seven. Measuring instead what each ecosystem
*added* over the same recent two years — 2024-09-21 to 2026-09-21:

| Last 2 years | Khronos | Vendor | Khronos share of new extensions |
| --- | ---: | ---: | ---: |
| Vulkan | 30 | 69 | **30%** |
| SYCL | 9 | 22 | **29%** |

The two ecosystems are currently producing Khronos and vendor extensions in
almost exactly the same proportion. SYCL's 8.5% stock is therefore not evidence
of a different governance balance; it is the arithmetic of a two-year-old
standardisation process sitting on top of a seven-year-old pile of vendor
extensions. Vulkan had `KHR` extensions from day one — its Khronos share was 33%
after one year and peaked at 47% after two — so it never had a backlog to work
off.

### When the proportions would converge

At the measured flows (4.5 KHR/year, 11.0 new vendor extensions/year) the
Khronos share of the SYCL surface rises from 8.5% towards an asymptote of **29%**:

| Khronos share | Reached in | Around |
| --- | ---: | --- |
| 15% | 3.2 years | 2029 |
| 20% | 8.7 years | 2035 |
| 25% | 28 years | 2054 |
| 33% (the Vulkan figure) | never at these rates | — |

So the answer is: the proposition does not hold today and will not hold on any
near horizon, but not because SYCL standardises a smaller fraction of new work —
it standardises about the same fraction. Reaching Vulkan's 33% requires KHR
output to overtake vendor output, not merely to keep pace with it, because the
starting stock is 91% vendor. The 29% asymptote is above the 20% mark and below
the Vulkan figure, and every year of delay raises the bar. At Vulkan's own KHR
publication rate the asymptote instead becomes 54–59% and the 33% mark is passed
around 2030 — see [What matching Vulkan's `KHR` rate would
change](#what-matching-vulkans-khr-rate-would-change).

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

### The `intel/llvm` data

The vendor-extension figures come from a clone of
[`intel/llvm`](https://github.com/intel/llvm) at `5a5fe36012b7` (2026-09-21,
branch `sycl`). The `supported`/`experimental` membership is the working-tree
contents of `sycl/doc/extensions/`; two of those entries are directories
(`supported/sycl_ext_intel_esimd` holds 2 extensions, `experimental/sycl_ext_matrix`
holds 2), and `supported/C-CXX-StandardLibrary.rst` is not a `sycl_ext_*`
extension and is excluded.

Creation dates and the directory history of each document come from a single
traversal recording every add, delete and rename under that path:

```sh
git log --reverse --diff-filter=ARD --name-status -M \
    --format='C|%cd' --date=short sycl -- sycl/doc/extensions/
```

Rename chains are followed so that a document moved `proposed` → `experimental`
→ `supported`, or renamed, keeps its original creation date. The same traversal,
replayed forward, gives the pool size at any past date. Committer dates are used
(137 of the last 3000 commits on `sycl` carry a backdated author date).

The vendor → KHR correspondences are not recorded anywhere: only
`sycl_ext_oneapi_device_default_context` names a `sycl_khr_*` extension, and no
`sycl_khr_*` document names a vendor extension. They were established by
comparing API names and semantics, and each is cited in the tables above.

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
* The absorption estimates assume the measured rates continue. They are linear
  extrapolations from 6 absorbed extensions over 22 months, so the confidence
  interval is wide: one extra absorption per year moves the frozen-pool estimate
  by roughly 7 years. They also say nothing about intent — an extension not yet
  proposed to Khronos may be one nobody intends to propose, and the split into
  "portable" and "vendor" in the tables above is a judgement about which of those
  could plausibly be standardised, not a statement from either project.
* Extensions may be absorbed in groups rather than one at a time. `sycl_khr_launch`
  covers two vendor extensions in a single PR, and `sycl_khr_group_interface`
  shows that Khronos may also replace a family of vendor extensions with a design
  that matches none of them, in which case the absorption count understates
  progress.
* The composition comparison counts documents, not features or lines. A single
  `KHR` extension can subsume several vendor extensions, and the two populations
  are not drawn from equivalent registries: Vulkan's is one curated list in
  `vk.xml`, while SYCL's "vendor" side is one implementation's `doc/extensions`
  tree, which excludes vendor extensions shipped by AdaptiveCpp or any other SYCL
  implementation. Counting those would lower the Khronos share further. The
  Vulkan maturity-matched figures are computed from the same committer-date
  dataset as the rest of `vulkan_table.md`, taking the Khronos share of all
  extensions published within *n* years of 2016-02-16.
* The Vulkan-rate scenarios substitute a different KHR publication rate into the
  same linear model and change nothing else. In particular they hold the
  absorption yield at the measured 0.67 pool extensions per published KHR
  extension and the pool's net growth at +4.5/yr; a project standardising three
  times as fast might well also attract more vendor extensions, or fewer. The
  baseline there is 4.9 KHR/yr (9 merges over the 22.2 months since the first
  merge), whereas the composition section uses 4.5/yr (9 merges over the last two
  years); the two conventions differ by 8% and are not interchangeable across
  tables.
* The two-year flow comparison uses the window 2024-09-21 → 2026-09-21 for both
  projects, counting first publication for Vulkan and, for SYCL, `sycl_khr_*`
  merges against first commits of new `intel/llvm` supported/experimental
  documents. The convergence projection extrapolates both of those rates
  unchanged and ignores absorption removing documents from the vendor side,
  which would raise the Khronos share faster than shown.

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
